<template>
  <div class="commemt">
    <h3>评论</h3>
    <!-- 文本框 -->
    <el-input
     class="textarea" 
     type="textarea" 
     :rows="2" 
     placeholder="请输入内容" 
     v-model="textarea"
     style="margin-bottom:20px;"
     ></el-input>
     <!-- 提交按钮 -->
     <el-button type="primary" style="margin-bottom:20px;float:right;">提交</el-button>
    <!-- 图片上传 -->
    <el-upload
      action="https://jsonplaceholder.typicode.com/posts/"
      list-type="picture-card"
      :on-preview="handlePictureCardPreview"
      :on-remove="handleRemove"
      class="upload"
      style="margin-bottom:20px;"
    >
      <i class="el-icon-plus"></i>
    </el-upload>
    <el-dialog :visible.sync="dialogVisible" size="tiny">
      <img width="100%" :src="dialogImageUrl" alt />
    </el-dialog>
    <!-- 评价列表 -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      textarea: "", //文本域
      dialogVisible:false, //
      dialogImageUrl:'' //图片路径
    };
  },
  methods:{
    // 点击已上传的文件链接时的钩子
    handlePictureCardPreview(file){
      this.dialogImageUrl = file.url;
      this.dialogVisible = true;
    },
    // 文件列表移除文件时的钩子
    handleRemove(file, fileList){}
  }
};
</script>

<style lang="less" scoped>
.commemt {
  h3 {
    font-weight: normal;
    padding-bottom: 20px;
  }
}
</style>

