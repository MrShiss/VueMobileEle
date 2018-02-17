
<template>
    <div id="entrylist1">
        <div v-for="l in list1" class="entrylist1">
            <div>
            	<p class="p1">{{l.title}}</p>
            	<p>{{l.subtitle}}</p>
            </div>
            <img style="width: 4rem;" :src="'https://fuss10.elemecdn.com/'+l.main_pic_hash+'.jpeg'" alt="" />
        </div>
    </div>
</template>

<script>
    export default{
        name:'entrylist1',
        data(){
        	return{
        		list1:[]       		
        	}
        },
        mounted(){
        	this.http.get('/eleapi/member/v1/discover?platform=2&block_index=0&latitude=35.026279&longitude=111.006989').then(res=>{
        		this.list1 = res.data[1]
        	})
        }
        
    }
</script>

<style scoped>
	#entrylist1{
		background-color: #ffffff;
		padding-top: 4rem;
	}
	.entrylist1 div{
		display: inline-block;
	}
	.entrylist1 div p:nth-of-type(1){
		color: #FF9900;
		font-size: 1.4rem;
	}
	.entrylist1 div p:nth-of-type(2){
		color: #999999;
	}
	.entrylist1 img{
		float: right;
	}
	.entrylist1{
		width: 50%;
		height: 7rem;
		display: inline-block;
		border-bottom: 1px solid #eee;
		border-right: 1px solid #eee;
		padding: 1rem 1rem;
	}
</style>
