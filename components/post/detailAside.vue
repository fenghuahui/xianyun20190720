<template>
  <div class="aside">
    <h3>相关攻略</h3>
    <!-- 列表 -->
    <el-row type="flex" class="list">
      <div>
        <img src="../../assets/images/1.jpg" >
      </div>
      <div>
        <div>我是标题</div>
        <span>2019-01-01 12:00 阅读:2</span>
      </div>
    </el-row>
  </div>
</template>

<script>
export default {
 
}
</script>

<style lang="less" scoped>
.aside{
  margin-left: 20px;
  h3{
    border-bottom: 1px solid #ccc;
    padding: 20px 0;
  }
  .list{
     padding: 20px 0;
     border-bottom: 1px solid #ccc;
     img{
       width: 80px;
       height: 80px;
       margin-right: 10px;
     }
     >div{
       height: 80px;
       &:nth-child(2){
       div{
         font-size: 18px;
       }
       span{
         color: #ccc;
         align-content: bottom;
       }
     }
     }
     
  }
 }
</style>

