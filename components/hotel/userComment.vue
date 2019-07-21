<template>
  <div class="container">
    <!-- 评论信息汇总 -->
    <div class="userCommentHeader">
      <h3 style="padding:10px 0;">10条真是用户评论</h3>
      <el-row>
        <el-col :span="5">
          <div>总评数：9</div>
          <div>好评数：1</div>
          <div>差评数：2</div>
        </el-col>
        <el-col :span="5" style="transform:translateY(115%)">
          <el-rate v-model="value" show-text></el-rate>
        </el-col>
        <el-col :span="5" style="transform:translateY(115%);color:#f7ba2a ">环境</el-col>
        <el-col :span="5" style="transform:translateY(115%);color:#f7ba2a ">产品</el-col>
        <el-col :span="4" style="transform:translateY(115%);color:#f7ba2a ">服务</el-col>
      </el-row>
    </div>
    <!-- 评论区 -->
    <div>
      <div class="commentArea" v-for="(item,index) in data" :key="index">
        <el-row>
          <el-col :span="3">
            <div>
              <span class="headPortrait">头像</span>
              <i style="color:#ff4d20;">LV.8</i>
            </div>
            <div>2019-6-26</div>
          </el-col>
          <el-col :span="21">
            <div style="padding:5px 0;color:#666;">{{item.content}}</div>
            <el-input v-model="input" placeholder="添加回复" style="width:87.5%;height:35px;"></el-input>
          </el-col>
        </el-row>
        <div class="commentAreaa" v-for="(items,index1) in item.followed" :key="index1">
          <el-row>
            <el-col :span="3">
              <div>
                <span class="headPortrait">头像</span>
                <i style="color:#ff4d20;">LV.8</i>
              </div>
              <div>2019-6-26</div>
            </el-col>
            <el-col :span="21">
              <div style="padding:5px 0;color:#666;">{{items.content}}</div>
              <el-input v-model="input" placeholder="添加回复" style="width:87.5%;height:35px;" @focus="styleChange"></el-input>
            </el-col>
          </el-row>
        </div>
      </div>
      <!-- 分页组件 -->
      <div class="block">
        <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="currentIndex"
          :page-sizes="[3, 6, 9, 12]"
          :page-size="pageSize"
          layout="total, sizes, prev, pager, next, jumper"
          :total="total"
        ></el-pagination>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  // name: "Item",
  // props: ["data"],
  props: {
    data: {
      type: Array,
      default: []
    }
  },
  data() {
    return {
      value: 4,
      input: "",
      currentIndex: 1,
      pageSize:3,
      total:5
    };
  },
  mounted() {
    console.log(this.data);
  },
  methods: {
    //   评论输入框被聚焦的时候
    styleChange(){
        
    },
    // 页容量改变时触发的事件
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    // 当前页改变时触发的事件
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    }
  },
};
</script>

<style lang="less" scoped>
.commentArea {
  margin: 50px 0;
  padding: 10px 0;
  .headPortrait {
    display: inline-block;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background: rgb(179, 88, 88);
    line-height: 50px;
    text-align: center;
    color: white;
  }
}
.commentAreaa {
  margin: 30px 0;
  padding: 10px 0 10px 50px;

  .headPortrait {
    display: inline-block;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background: rgb(179, 88, 88);
    line-height: 50px;
    text-align: center;
    color: white;
  }
}
</style>

