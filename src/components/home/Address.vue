
<template>
    <div id="address">
        <navbar>选择收货地址</navbar>
        <div class="address">
	        <div class="address-s">
	            <i class="fa fa-search"></i>
	            <input type="text" placeholder="请输入地址" />
	        </div>
	    </div>
        <p class="now-address">当前地址</p>
        <div class="now-address-menu">
        	<span class="now-address-menu-1">乌鲁木齐齐齐哈尔乌鲁木齐齐齐哈尔乌鲁木齐齐齐哈尔</span>
        	<a style="font-size: 1.2rem;color: #2495FF;float: right;padding-right: 1.5rem;" href="">
        		<i class="fa fa-bullseye"></i>
        		<span>重新定位</span>
        	</a>
        </div>       
    </div>
</template>

<script>
    import Navbar from '../Navbar'
    export default{
        name:'address',
        components:{
            Navbar
        }
        
    }
</script>

<style scoped>
	.address{
		background-color: white;
		padding: 1rem 1.2rem;
		cursor: default;
	}
	.address-s{
		padding: 0.8rem;
		background-color: #F2F2F2;
	}
	.address-s input{
		width: 90%;
		border: none;
		background-color: #F2F2F2;
		color: #C2C2C2;
	}
	.address-s i{
		color: #999999;
		font-size: 1.2rem;
	}
	.now-address{
		width: 100%;
		padding: 1rem;
		background-color: #F2F2F2;
		font-size: 1.2rem;
		color: #8C668C;
		cursor: default;
	}
	.now-address-menu{
		padding: 0.8rem;
		background-color: white;
		cursor: default;
	}
	.now-address-menu .now-address-menu-1{
		display: inline-block;
		width: 70%;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		font-size: 1.3rem;
		font-weight: bold;
	}
</style>
