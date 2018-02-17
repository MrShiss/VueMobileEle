<template>
    <div id="home">
        <header>
        	<div class="dz-tq">
        		<router-link class="dz" to="/address">
	        	        <i class="fa fa-map-marker"></i>
	        	        <span>{{sites.name}}</span>
	        	        <i style="float: right;padding:0.2rem 1.5rem 0 0;" class="fa fa-caret-down"></i>
        		</router-link>       	    
        	    <div class="tq">
        	    	<div>
        	    		<h5>{{weather.temperature}}°</h5> 
        	       		<p>{{weather.description}}</p>
        	    	</div>
        	    	<img :src="'https://fuss10.elemecdn.com/' + weather.image_hash + '.png'"/>
        	    </div>
        	    
        	</div>
        	<router-link class="header-search" to="/search">
        		<i class="fa fa-search"></i>
        		<span>搜 索 商 家，搜 索 名 称</span>
        	</router-link>
        	<router-link v-if="isshow" class="header-search-fixed" to="/search">
        		<i class="fa fa-search"></i>
        		<span>搜 索 商 家，搜 索 名 称</span>
        	</router-link>
    	    <div class="header-food">
    	    	<ul>
    	    		<router-link v-for="(food,i) in foods" :key="food.search_word" to="">
    	    			<li>{{food.search_word}}</li>
    	    		</router-link>
    	    	</ul>
    	    </div>
        </header>
        <!--轮播-->
        <main>
		    <swiper auto height="13rem" dots-position="center">
			     <swiper-item class="black">
			      	<router-link to="">
			      		<div v-for="e in entry1" class="swiper">
			      			<img :src="'https://fuss10.elemecdn.com/'+e.image_hash+'.jpeg'"/>
			      			<p>{{e.name}}</p>
			      		</div>			      		
			      	</router-link>
			     </swiper-item>
			     <swiper-item class="black">
			      	<router-link to="">
			      		<div v-for="e in entry2" class="swiper">
			      			<img :src="'https://fuss10.elemecdn.com/'+e.image_hash+'.jpeg'"/>
			      			<p>{{e.name}}</p>
			      		</div>
			      	</router-link>
			     </swiper-item>
		    </swiper>
		    <img style="margin-left: 1.1rem; width: 94%;" src="https://fuss10.elemecdn.com/3/12/05997b77c8cb8adf82298b8a39434png.png?imageMogr/thumbnail/!710x178r/gravity/Center/crop/710x178/"/>
		    <hotsail></hotsail>
	    </main>
	    <recome></recome>
	    <div style="height: 4.5rem;"></div>
    </div>
</template>

<script>
	import Recome from './/home/Recome'
	import Hotsail from './home/Hotsail'
	import { Swiper, SwiperItem } from 'vux'
	export default {
    name:'home',
    components: {
    Swiper,
    SwiperItem,
    Hotsail,
    Recome
  },
    data(){
    	return{
    			sites:[],
    			foods:[],
    			weather:[],
    			weatherimg:'',
    			entry1:[],
    			entry2:[],
    			isshow:false
    	}
    },
    methods:{
    	didScroll(){
            var bodyH = document.body.clientHeight;//页面的总高度
            var scrollTop = document.scrollingElement.scrollTop;//页面滚动时被卷去的高度
            var windowH = document.documentElement.clientHeight;//可视页面的高度
            if (scrollTop >= 50) {
				this.isshow = true
            }else{
            	this.isshow = false
            }
        }
    },
    mounted () {
    	window.onscroll = this.didScroll
//      console.log('获取地址');
        this.http.get('/eleapi/v2/pois/ww8p3nhuhtsh').then(res=>{
//      	console.log(res.data)
             this.sites = res.data;           
        });
//      console.log('获取天气');
        this.http.get('/eleapi/bgs/weather/current?latitude=35.42574&longitude=111.30214').then(res=>{
//      	console.log(res.data)
             this.weather = res.data;
        });
//      console.log('获取热搜');
        this.http.get('/eleapi/shopping/v3/hot_search_words?latitude=37.87059&longitude=112.550667').then(res=>{
//      	console.log(res.data)
             this.foods = res.data;           
        });
//      console.log('获取轮播');
        this.http.get('/eleapi/shopping/v2/entries?latitude=35.42574&longitude=111.30214&templates[]=main_template').then(res=>{
//      	console.log(res.data)
             	this.entry1 = res.data[0].entries.slice(0,8); 
             	this.entry2 = res.data[0].entries.slice(8); 
        });
    }
   }
</script>

<style scoped>
	header{
		background-color: #0092ff;
		color: #fff;
		overflow: hidden;
	}
	.dz-tq{
		display: flex;
		justify-content: space-between;
		padding: 1rem;
		color: white;
	}
	.dz{
		width: 50%;
		font-size: 1.5rem;
		font-weight: bold;
		position: relative;
	}
	.dz span{
		display: inline-block;
		width: 80%;
		overflow: hidden;
		text-overflow:ellipsis;
		white-space: nowrap;
		position: absolute;
		padding-left: 0.5rem;
	}
	.tq{
		font-size: 1rem;
		cursor: default;
		position: relative;
	}
	.tq div{
		width: 2rem;
		position: absolute;
		right: 2rem;
		text-align: center;
	}
	img{
		width: 2rem;
		
	}
	.header-search{
		display: flex;
		align-items: center;
		justify-content: center;
		width: 92%;
		height: 3rem;
		background-color: #fff;
		color: #666;
		font-size: 1rem;
		margin-left: 1.2rem;
		min-width: 50px;
	}
	.header-search i{
		margin-right: 0.5rem;
		font-size: 1rem;
	}
	.header-food{
		overflow: hidden;
		overflow-x: auto;
		padding-bottom: 0.5rem;
	}
	.header-food ul{
		width: 140%;
		margin-top: 1rem;
		padding-bottom: 1rem;
		font-size: 1.2rem;
		height: 2rem;		
		overflow: hidden;
		overflow-x: auto;
		padding-left: 1rem;
	}
	.header-food li{
		margin-right: 1rem;
		display: inline-block;
	}
	main{
		background-color: #ffffff;
	}
	.swiper{
		display: inline-block;
		width: 25%;
		text-align: center;
		color: #666666;
		margin: 0.5rem 0; 
	}
	.swiper img{
		width: 40%;
	}
	.header-search-fixed{
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 4rem;
		background-color: #fff;
		color: #666;
		font-size: 1rem;
		min-width: 50px;
		position: fixed;
		top: 0;
		z-index: 999;
		border-top: 0.6rem solid dodgerblue;
		border-bottom: 0.6rem solid dodgerblue;
		border-right: 1.5rem solid dodgerblue;
		border-left: 1.5rem solid dodgerblue;
	}
	.header-search-fixed i{
		margin-right: 0.5rem;
		font-size: 1rem;
	}
</style>
