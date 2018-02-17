
<template>
    <div id="entrylist2">
        <div class="list2-header">
        	<div>
        		<i class="fa fa-long-arrow-right fa-2x" aria-hidden="true"></i>
        		<i style="font-size: 2rem;color: red;" class="fa fa-thumbs-o-up" aria-hidden="true"></i>
        		<h2 style="display: inline-block;">{{title}}</h2>
        		<i class="fa fa-long-arrow-left fa-2x" aria-hidden="true"></i>
        		<p>你的口味，我都懂的</p>
        	</div>
        </div>
        <div class="list2-body">
    		<div>
    			<img width="100%" :src="'https://fuss10.elemecdn.com/'+list2.image_path+'.jpeg'" alt="" />
    			<p style="height: 1.5rem;overflow: hidden;">{{list2.name}}</p>
    			<p style="color: #FF5339;">{{list2.price}}</p>
    			<span>{{list2.discount_rate}}折</span>
    		</div>
    		<div>
    			<img width="100%" :src="'https://fuss10.elemecdn.com/'+list2_1.image_path+'.jpeg'" alt="" />
    			<p style="height: 1.5rem;overflow: hidden;">{{list2_1.name}}</p>
    			<p style="color: #FF5339;">{{list2_2.price}}</p>
    			<span>{{list2_1.discount_rate}}折</span>
    		</div>
    		<div>
    			<img width="100%" :src="'https://fuss10.elemecdn.com/'+list2_2.image_path+'.jpeg'" alt="" />
    			<p style="height: 1.5rem;overflow: hidden;">{{list2_2.name}}</p>
    			<p style="color: #FF5339;">{{list2_2.price}}</p>
    			<span>{{list2_2.discount_rate}}折</span>
    		</div>
    	</div>
    	<p style="color: #999999; margin-top: 1rem;">查看更多  ></p>
    	<div style="height: 4.5rem;"></div>
    </div>
</template>

<script>
    export default{
        name:'entrylist2',
        data(){
        	return{
        		title:'',
        		list2:[],
        		list2_1:[],
        		list2_2:[]
        	}
        },
        mounted(){
        	this.http.get('/eleapi/shopping/v1/sale_list_index?type=special_food&latitude=35.026279&longitude=111.006989&params={}').then(res=>{
        		this.title = res.data.page_title
        		this.list2 = res.data.query_list[0].foods[0]
        		this.list2_1 = res.data.query_list[1].foods[0]
        		this.list2_2 = res.data.query_list[2].foods[0]
//      		console.log(this.list2)
        	})
        }
        
    }
</script>

<style scoped>
	#entrylist2{
		margin-top: 1rem;
		background-color: #ffffff;
		text-align: center;
		height: 23rem;
	}
	.list2-header{
		padding: 1rem 0;
	}
	.list2-header p{
		color: #999999;
		margin-bottom: 0.5rem;
	}
	.list2-body div{
		width: 32%;
		position: relative;
		display: inline-block;
	}
	.list2-body div p{
		text-overflow: ellipsis;
		white-space: nowrap;
	}
	.list2-body div span{
		position: absolute;
		top: 0;
		left: 0;
		color: white;
		background-color: #413D3C;
	}
</style>
