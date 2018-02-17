
<template>
    <div id="hotsail">
        <div class="hot-1">
        	<div>
        		<h3>热卖套餐</h3>
	            <p>销量最高，好评最多</p>
	            <p>TOP 100 ></i></p>
        	</div>
             <img style="width: 40%;" src="https://fuss10.elemecdn.com/e/ee/df43e7e53f6e1346c3fda0609f1d3png.png?imageMogr/thumbnail/!282x188r/gravity/Center/crop/282x188/"/>
        </div>
        <div class="hot-2">
            <div class="hot-2-2" v-for="item in items">
            	<h3>{{item.name}}</h3>
            	<p><span>{{item.describe}}</span></p>
            	<img style="width: 80%;" :src="item.img"/>
            </div>
        </div>
    </div>
</template>

<script>
    export default{
        name:'hotsail',
        data(){
        	return{
        		items:[
        			{
        				name:'天天特价',
        				describe:'低至一折',
        				img:'https://fuss10.elemecdn.com/5/06/ddb537220b8c56d4ef6ae22718984png.png?imageMogr/thumbnail/!232x154r/gravity/Center/crop/232x154/'
        			},
        			{
        				name:'吃货狂欢',
        				describe:'随叫随到',
        				img:'https://fuss10.elemecdn.com/a/98/8010e87e876a7bf137597bf7fd324png.png?imageMogr/thumbnail/!232x154r/gravity/Center/crop/232x154/'
        			},
        			{
        				name:'品质优选',
        				describe:'尖货来袭',
        				img:'https://fuss10.elemecdn.com/a/b5/dcb5bff74242e06b3c2efee1cbffcpng.png?imageMogr/thumbnail/!232x154r/gravity/Center/crop/232x154/'
        			}
        		]
        	}
        }
        
    }
</script>

<style scoped>
	.hot-1{
		width: 94%;
		margin-top: 0.5rem;
		margin-left: 1.1rem;
		background-color: #F6F6F6;
		position: relative;
		height: 10rem;
		padding: 1rem ;
	}
	.hot-1 div{
		display: inline-block;
	}
	.hot-1 div h3{
		font-size: 1.5rem;
		padding-bottom: 0.5rem;
		color: #333333;
	}
	.hot-1 div p:nth-of-type(1){
		font-size: 1.2rem;
		color: #777777;
		padding-bottom: 0.5rem;
	}
	.hot-1 div p:nth-of-type(2){
		font-size: 1rem;
		font-weight: bold;
		color: #AF8260;
	}
	.hot-1 img{
		float: right;
	}
	.hot-2{
		margin-left: 1.1rem;
		margin-top: 0.5rem;
		padding-bottom: 1rem;
	}
	.hot-2-2{
		width: 31%;
		display: inline-block;
		background-color: #F6F6F6;
		position: relative;
		height: 12rem;
		margin-right: 0.67rem;
		text-align: center;
	}
	.hot-2-2 h3{
		padding-top: 0.9rem;
		font-size: 1.5rem;
		color: #333333;
		margin-bottom: 0.5rem;
	}
	.hot-2-2 p{
		color: #878787;		
	}
	.hot-2-2 p span{
		border: 1px solid #878787;
		padding: 0 0.1rem;
	}
	.hot-2-2 img{
		margin-top: 2rem;
	}
</style>
