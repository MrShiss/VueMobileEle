<!-- app.vue -->
<template>
  <div id="app">
    <ul id="tabbar">
    	<router-link class="tabbar" to="/">
    		<li style="color: dodgerblue;" @click="hah" class="tabbar-l">
	    		<i class="fa fa-internet-explorer fa-2x"></i>
	    		<span class="tabbar-s">外卖</span>
    		</li>
    	</router-link>
    	<router-link class="tabbar" to="/find">
    		<li @click="hah1" class="tabbar-l">
	    		<i class="fa fa-bullseye fa-2x"></i>
	    		<span class="tabbar-s">发现</span>
    		</li>
    	</router-link>
    	<router-link class="tabbar" to="/order">
    		<li @click="hah2" class="tabbar-l">
	    		<i class="fa fa-file-text-o fa-2x"></i>
	    		<span class="tabbar-s">订单</span>
    		</li>
    	</router-link>
    	<router-link class="tabbar" to="/my">
    		<li @click="hah3" class="tabbar-l">
	    		<i class="fa fa-user fa-2x"></i>
	    		<span class="tabbar-s">我的</span>
    		</li>
    	</router-link>
    </ul>
    <router-view></router-view>
  </div>
</template>

<script>
	export default{
		methods:{
			hah(){
				var li = document.getElementsByClassName('tabbar-l')
				li[0].style.color = 'dodgerblue'
				li[1].style.color = 'inherit'
				li[2].style.color = 'inherit'
				li[3].style.color = 'inherit'
			},
			hah1(){
				var li = document.getElementsByClassName('tabbar-l')
				li[0].style.color = 'inherit'
				li[1].style.color = 'dodgerblue'
				li[2].style.color = 'inherit'
				li[3].style.color = 'inherit'
			},
			hah2(){
				var li = document.getElementsByClassName('tabbar-l')
				li[0].style.color = 'inherit'
				li[1].style.color = 'inherit'
				li[2].style.color = 'dodgerblue'
				li[3].style.color = 'inherit'
			},
			hah3(){
				var li = document.getElementsByClassName('tabbar-l')
				li[0].style.color = 'inherit'
				li[1].style.color = 'inherit'
				li[2].style.color = 'inherit'
				li[3].style.color = 'dodgerblue'
			}
		}
	}
</script>

<style>
#tabbar{
	height: 4.5rem;
	width: 100%;
	position: fixed;
	bottom: 0;
	display: flex;
	justify-content: center;
	align-content: space-between;
	z-index: 999;
	background-color: #ffffff;
	padding-top: 0.5rem;
	border-top: 1px solid lightgray;
	color: #666666;
}
.tabbar .fa-2x,.tabbar-s{
	display: block;
}
.tabbar{
	display: inline-block;
	width: 25%;
}
.tabbar .tabbar-l{
	text-align: center;
	font-size: 1rem;
	cursor: pointer;
}
</style>
