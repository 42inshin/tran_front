<template>
	<div id="wrapper">
		<div class="pong_canvas">
			<canvas id="pong" width="700" height="500"></canvas>
		</div>
	</div>
</template>

<script setup lang="ts">
// import io from "socket.io-client"
// import { ref } from "vue";
// import { useCookies } from "vue3-cookies";

// let socket: any;
// const { cookies } = useCookies();

// var position = {
// 	x: 0,
// 	y: 200
// }

// const socketOptions = {
//    transportOptions: {
//      polling: {
//        extraHeaders: {
//          Authorization: "Bearer " + cookies.get('jwt')
//        }
//      }
//    }
// };

// socket = io('http://localhost:5000', socketOptions);
// socket.on('connect', () => {
//     socket.emit('gametest');
// });

import TestGame from "./test_game";
import { onMounted } from "vue";

var	get_mous: number;

onMounted(() => {
	const canvas: HTMLCanvasElement = document.getElementById(
	"pong"
	) as HTMLCanvasElement;
	if (!canvas) return console.error("canvas is undefined");
	const test = new TestGame(canvas);
	canvas.addEventListener("mousemove", getMousePos);

	function getMousePos(evt: MouseEvent) : void {
		// let rect = this.canvas.getBoundingClientRect();

		get_mous =  evt.clientY - 180;

		// console.log(this.left_user);
	}
	const interval = setInterval(() => {
	test.game(get_mous);
	}, 20);
});

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
