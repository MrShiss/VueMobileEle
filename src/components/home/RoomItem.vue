
<template>
    <div id="roomitem">
        <div class="roomitem">
        	<img v-if="item.image_path.slice(-4) == 'jpeg'" width="50rem" :src="'https://fuss10.elemecdn.com/'+item.image_path+'.jpeg'"/>
        	<img v-if="item.image_path.slice(-3) == 'png'" width="50rem" :src="'https://fuss10.elemecdn.com/'+item.image_path+'.png'"/>
        	<div class="roomitem-1">
	            <h3>{{item.name}}</h3>
	            <p>
	            	<span style="color: darkorange;">评分：{{item.rating}}</span>
	            	<span>月售{{item.recent_order_num}}单</span>
	            </p>
	            <p>
	            	<span>{{item.piecewise_agent_fee.description}}</span>
	            	<span class="pull-right">{{item.distance}}m</span>
	            	<span style="padding-right: 0.3rem;" class="pull-right">{{item.order_lead_time}}分钟 |</span>
	            </p>
	            <div v-if="item.recommend.reason == '口碑人气好店'" style="margin-top: 0.5rem;padding-bottom: 0.5rem;width: 100%;">
	            	<img width="15rem" :src="'https://fuss10.elemecdn.com/'+item.recommend.image_hash+'.png'" alt="" />
	            	<p style="font-size: 0.8rem;color: red;">{{item.recommend.reason}}</p>
	            </div>
	            <div class="roomitem-2">
            		<p v-for="i in item.activities">
            			<span v-bind:style="{color:'#' + i.icon_color}">{{i.icon_name}}</span>
            			<span>{{i.description}}</span>
            		</p>
        		</div>
	        </div>
        </div>
    </div>
</template>

<script>
    export default{
        name:'roomitem',
        props:['item']
        
    }
</script>

<style scoped>
	#roomitem,.roomitem{
		width: 100%;
	}
	.roomitem{
		border-bottom: 1px solid #eee;
		margin-bottom: 1rem;
		padding: 1.5rem 0 0 1rem;
	}
	.roomitem img,div{
		display: inline-block;
	}
	.roomitem img{
		border: 1px solid #eee;
		margin-right: 1rem;
		float: left;
	}
	.roomitem .roomitem-1{
		width: 80%;
	}
	.roomitem div p{
		color: #666;
	}
	.roomitem div p span{
		padding-bottom: 0.3rem;
		font-size: 0.9rem;
	}
	.roomitem div h3{
		color: #333;
		padding-bottom: 0.3rem;
	}
	.roomitem-2{
		height: 3.5rem;
		overflow: auto;
		border-top: 1px solid #eee;
		padding-top: 0.5rem;
		width: 100%;
	}
	.roomitem-2 p{
		margin-bottom: 0.3rem;
		font-size: 0.8rem;
	}
</style>
