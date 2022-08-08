<template>
	<div id="wrapper">
		<div class="pong_canvas">
			<canvas id="pong" width="700" height="500"></canvas>
		</div>
	</div>
</template>

<script setup lang="ts">
import io from "socket.io-client"
import { ref } from "vue";
import { useCookies } from "vue3-cookies";

import TestGame from "./test_game";
import { onMounted } from "vue";

let socket: any;
const { cookies } = useCookies();
var	paddle_side: number;
// var position = {
// 	x: 0,
// 	y: 200
// }

const socketOptions = {
   transportOptions: {
     polling: {
       extraHeaders: {
         Authorization: "Bearer " + cookies.get('jwt')
       }
     }
   }
};

socket = io('http://localhost:5000', socketOptions);
socket.on('connect', () => {
    socket.emit('rank_battle');
});

socket.on('get_paddle', (paddle: number) => {
	paddle_side = paddle;
})
// socket.on('start_battle', (room_num: string) => {
// 	console.log("paddle: " + paddle_side);
// 	console.log("room: " + room_num);
// 	console.log("pos: " + paddlePos);
// 	const interval = setInterval(() => {
// 	socket.emit('paddleDeliver', paddlePos, paddle_side, room_num);
// 	}, 30);
// })

var	paddlePos: number;
paddlePos = 200;
var test : TestGame;
var canvas : HTMLCanvasElement;
onMounted(() => {
	canvas = document.getElementById("pong") as HTMLCanvasElement;
	if (!canvas) return console.error("canvas is undefined");
	test = new TestGame(canvas);
	canvas.addEventListener("mousemove", getMousePos);
	function getMousePos(evt: MouseEvent) : void {
		paddlePos =  evt.clientY - 180;
	}
	// return () => clearInterval(interval);
	// const interval = setInterval(() => {
		// test.game(paddlePos);
	// }, 20);
});

socket.on('start_battle', (room_num: string) => {
	console.log("paddle: " + paddle_side);
	console.log("room: " + room_num);
	console.log("pos: " + paddlePos);
	const interval = setInterval(() => {
		socket.emit('paddleDeliver', {paddleSide:paddle_side,paddlePos: paddlePos, roomNum: room_num});
		}, 50);
})

socket.on('gameData', (pos: number)=>{
	//console.log("아무것도하기싫어 : " + pos);
	test?.game(pos);
})

</script>

<style>
/* canvas {
	background: none;
} */
.pong_canvas{
	display: inline-block;
	outline: 8px solid	#fff;
	width: 700px;
	height: 500px;
}

#wrapper{
	display: flex;
	justify-content: center;
	align-items: center;
    width: 860px;
    height: 640px;
    background-color: rgb(50, 53, 91);
    border-radius: 10px;
}
</style>
