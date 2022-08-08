<template>
	<div class="buttonBox">
		<nav>
			<RouterLink to="/battle">
				<button class="rank_button">
				<p class="rank_text">🏆</p>
				<p class="rank_text">랭크 게임</p>
				</button>
			</RouterLink>
		</nav>
	</div>
</template>

<style>
.buttonBox{
	width: 1240px;
	height: 824px;

	position: absolute;
	left: 0%;
	right: 0%;
	top: 0%;
	bottom: 0%;

	background: #272843;
	box-shadow: 15px 15px 40px rgba(0, 0, 0, 0.1);
	border-radius: 30px;
}
.rank_button{
	width: 228px;
	height: 148px;

	position: absolute;
	left: 0%;
	right: 0%;
	top: 0%;
	bottom: 0%;

	background: linear-gradient(292.57deg, #A52435 0%, #F25E72 100%);
	box-shadow: 15px 15px 40px rgba(0, 0, 0, 0.2);
	border-radius: 30px;
}
.rank_text{
	/* position: absolute; */
	/* left: 12.72%;
	right: 12.72%;
	top: 16.33%;
	bottom: 15.65%; */

	font-family: 'Do Hyeon';
	font-style: normal;
	font-weight: 400;
	font-size: 35px;
	line-height: 44px;
	/* display: flex; */
	align-items: center;
	text-align: center;

	color: #FFFFFF;
}
</style>
