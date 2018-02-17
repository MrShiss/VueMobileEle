
<template>
    <div id="find">
        <navbar>发现</navbar>
        <entrylist1></entrylist1>
        <img style="width: 100%;margin-top: 1rem;" src="https://fuss10.elemecdn.com/b/6d/656006edcd86033a1b32b23ddea37jpeg.jpeg" alt="" />
        <entrylist2></entrylist2>
        <entrylist2></entrylist2>
        <entrylist2></entrylist2>
    </div>
</template>

<script>
    import Navbar from './Navbar'
    import Entrylist1 from './find/Entrylist1'
    import Entrylist2 from './find/Entrylist2'
    export default{
        name:'find',
        components:{
            Navbar,
            Entrylist1,
            Entrylist2
        }
        
    }
</script>

<style scoped>
</style>
