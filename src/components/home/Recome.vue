
<template>
    <div id="recome">
    <h2 style="font-size: 1.5rem;margin-bottom: 1rem;padding: 1rem 0 0 1rem;">推荐商家</h2>
        <div class="">
        	<div class="loading">
                <span v-if="status == 'loading'" class="fa fa-spinner fa-pulse fa-3x fa-fw"></span>
                <span v-if="status == 'fail'">加载失败...</span>
            </div>
            <div v-if="status == 'success'">
                <roomitem v-for="item in roomlist" :item="item" :key="item.name"></roomitem>
            </div>
            <div v-if="status == 'success'" class="load-more">
                <span class="fa fa-spinner fa-pulse fa-2x fa-fw"></span>
                	正在加载更多
            </div>
        </div>
    </div>
</template>

<script>
	import Roomitem from './Roomitem'
    export default{
        name:'recome',
        components:{
        	Roomitem
        },
        data(){
        	return{
        		roomlist:[],
        		status:'loading',
        		isLoading: false
        	}
        },
        methods: {
        // 当页面发生滚动时调用的函数
        didScroll(){
            var bodyH = document.body.clientHeight;//页面的总高度
            var scrollTop = document.scrollingElement.scrollTop;//页面滚动时被卷去的高度
            var windowH = document.documentElement.clientHeight;//可视页面的高度
            if (windowH+scrollTop >= bodyH-30) {
//              console.log('加载更多');
                if (!this.isLoading) {
                    this.loadMore();
                }
            }
        },
        loadMore(){
            this.isLoading = true;
            this.http.get('/eleapi/shopping/restaurants?latitude=38.01135&longitude=112.44299&offset=0&limit=20&extras[]=activities&terminal=h5&extra_filters=home',{
                params:{offset:this.roomlist.length/10}
            })
            .then(res=>{
                if (res.data) {
                    this.roomlist = this.roomlist.concat(res.data);
                }
                this.isLoading = false;
            },err=>{
                this.isLoading = false;   
            }) 
        }
    },
	    mounted () {
	    window.onscroll = this.didScroll;
//	    console.log('获取房间列表');
	    this.http.get('/eleapi/shopping/restaurants?latitude=38.01135&longitude=112.44299&offset=0&limit=20&extras[]=activities&terminal=h5&extra_filters=home').then(res=>{
	       
	        if (res.data.length > 1) {
	            this.status = 'success';
	            this.roomlist = res.data;
	            
	        } else {
	            this.status = 'fail';
	        }
	    },err=>{
	        console.log(err);
	        this.status = 'fail'
	    });
    }
    }
</script>

<style scoped>
	#recome{
		background-color: #ffffff;
		margin-top: 1rem;
	}
	.loading{
    text-align: center;
	}
	.load-more{
	    text-align: center;
	    font-size: 1.2rem;
	}
</style>
