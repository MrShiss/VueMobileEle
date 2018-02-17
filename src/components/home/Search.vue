
<template>
    <div id="search">
    	<div class="search">
    	    <span @click="back" class="fa fa-angle-left fa-3x back pull-left"></span>
	        <div>
	        	<i class="fa fa-search"></i>
	        	<input type="text" placeholder="输入商家、商品信息" />
	        </div>
	        <h3>搜索</h3>
    	</div>
        <div class="search-hot">
            <h3>热门搜索</h3>
            <div>
            	<span v-for="l in list">{{l.word}}</span>
            </div>
            
        </div>
    </div>
</template>

<script>
    export default{
        name:'search',
        data(){
        	return{
        		list:[]
        	}
        },
        methods: {
        back(){
            window.history.back();
           }
        },
        mounted () {
//      console.log('获取热搜');
        this.http.get('/eleapi/shopping/v3/hot_search_words?latitude=37.87059&longitude=112.550667').then(res=>{
//      	console.log(res.data)
             this.list = res.data;           
        });
    }
        
    }
</script>

<style scoped>
	.search{
		background-color: #ffffff;
		padding-top: 0.5rem;
		display: flex;
		justify-content: center;
		align-items: center;
		
	}
	.search span{
		padding: 0.2rem 1rem;
		color: #999999;
	}
	.search div,h3{
		display: inline-block;
	}
	.search div{
		margin-top: 0.2rem;
		padding: 0.5rem;
		background-color: #F8F8F8;
		width: 70%;
		color: #C5C5C5;
	}
	.search div input{
		width: 90%;
		background-color: #F8F8F8;
		border: none;
		color: #C5C5C5;
	}
	.search h3{
		margin-left: 1rem;
		color: #333333;
		font-size: 1.5rem;
	}
	.search-hot{
		background-color: #ffffff;
		padding: 2.5rem 1rem 0 1rem;
	}
	.search-hot h3{
		font-size: 1.5rem;
		color: #666;
	}
	.search-hot div{
		padding-top: 2rem;
		width: 100%;
		display: flex;
		flex-wrap: wrap;
	}
	.search-hot span{
		display: inline-block;
		margin-right: 1rem;
		margin-bottom: 1rem;
		padding: 0.5rem;
		background-color: #f7f7f7;
		font-size: 1.2rem;
		color: #666;
	}
</style>
