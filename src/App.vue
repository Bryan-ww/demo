<template>
<div id="app">
    <el-container style="height:100%;">
      <el-aside width="200px">
        <CommonAside></CommonAside>
      </el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
</div>
</template>
<script>
import CommonAside from"@/components/CommonAside";

export default  {
  name: 'App',
  components:{CommonAside}
}

</script>

<style scoped>
#app{
  height: 100vh;
}
 .el-header {
    background-color: #B3C0D1;
    color: #333;
  }
  
  .el-aside {
    /* color: #333; */
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
  }
  
  body > .el-container {
    margin-bottom: 40px;


  }
  
  
</style>
