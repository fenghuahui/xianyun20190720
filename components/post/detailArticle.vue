<template>
  <div class="mian">
    <h1>{{postDetail.title}}</h1>
    <!-- <hr/> -->
    <el-row type="flex" class="readNum">
      <span>发布时间:{{postDetail.city.created_at}}</span>
      &nbsp;&nbsp;&nbsp;
      <span>阅读：{{postDetail.watch}}</span>
    </el-row>
    <!-- 内容 -->
    <div class="content" v-html="postDetail.content"></div>
    <!-- 收藏 -->
    <el-row type="flex" class="tool">
      <div class="comment">
        <i class="iconfont iconpinglun"></i>
        <p>评论（100）</p>
      </div>
      <div class="collect">
        <i class="iconfont iconstar1"></i>
        <p>收藏</p>
      </div>
      <div class="share">
        <i class="iconfont iconfenxiang"></i>
        <p>分享</p>
      </div>
      <div class="like">
        <i class="iconfont iconding"></i>
        <p>点赞（0）</p>
      </div>
    </el-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: 4,
      postDetail: {
        city: ""
      }
    };
  },
  mounted() {
    // 请求文章详情接口
    this.$axios({
      url: "posts",
      params: {
        id: this.id
      }
    }).then(res => {
      console.log(res);
      // this.postDetail = res.data.data[0].content
      this.postDetail = res.data.data[0];
    });
  }
};
</script>

<style lang="less" scoped>
.mian {
  .tool {
    padding: 50px 0 30px 0;
    // text-align: center;
    // margin: 0 auto;
    font-size: 14px;
    color: #666;
    >div{
      padding: 0 20px;
      height: 58px;
      // line-height: 58px;
      text-align: center;
      i{
        color: orange;
        font-size: 28px;
        margin-bottom: 8px;
      }
    }
  }
  h1 {
    padding: 20px 0;
    border-bottom: 1px solid #ccc;
  }
  .readNum {
    color: #666;
    padding: 20px 0;
  }
  .content {
    /deep/ p {
      span {
        img {
          width: 100%;
        }
      }
    }
  }
}
</style>

