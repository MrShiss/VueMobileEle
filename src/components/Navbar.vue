<template>
	<header class="navbar">
		<span @click="back" class="fa fa-angle-left back"></span>
		<slot></slot>
	</header>
</template>

<script>
	export default{
		methods: {
        back(){
            window.history.back();
        }
    }
	}

</script>

<style>
	.navbar{
		text-align: center;
		width: 100%;
		height: 4rem;
		position: fixed;
		top: 0;
		left: 0;
		z-index: 999;
		background-color: #0092FF;
		font-weight: 700;
		font-size: 1.5rem;
		color: #fff;
		line-height: 4rem;
		position: relative;
	}
	.navbar span{
		position: absolute;
		padding: 1rem;
		left: 0.5rem;
		top: 0.2rem;
		cursor: pointer;
	}
</style>