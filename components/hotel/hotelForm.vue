<template>
  <section>
    <div class="container">
        <!-- 头部导航信息 -->
      <div class="title">
        <nuxt-link to="/">
          <span>酒店</span>
        </nuxt-link>
        <i class="el-breadcrumb__separator el-icon-arrow-right"></i>
        <nuxt-link to="/">
          <span>南京酒店</span>
        </nuxt-link>
        <i class="el-breadcrumb__separator el-icon-arrow-right" ></i>
        <span>日出花园艺术酒店(南京仙林大学城店)</span>
      </div>
      <!-- 酒店基本资料 -->
      <div class="hotelMessage">
        <h4>
          好来商务宾馆
          <span>
            <i class="iconfont iconhuangguan" style="color:#ff9900"></i>
            <i class="iconfont iconhuangguan" style="color:#ff9900"></i>
            <i class="iconfont iconhuangguan" style="color:#ff9900"></i>
            <i class="iconfont iconhuangguan" style="color:#ff9900"></i>
            <i class="iconfont iconhuangguan" style="color:#ff9900"></i>
          </span>
        </h4>
        <div style="color:#666;">hao lai ge shang wu hotel</div>
        <div style="color:#666;">
          <i class="iconfont iconlocation"></i>
          <span>高淳县淳溪镇镇兴路118号(高淳县委党校对面)</span>
        </div>
      </div>
      <!-- 酒店基本布局图片展示 -->
      <div class="showPicture">
        <el-row>
          <el-col :span="16">
            <img src="../../images/1 (1).jpeg" style="height:360px;width:640px;" />
          </el-col>
          <el-col :span="8">
            <img src="../../images/1.jpeg" style="width:160px;margin-bottom:10px;" />
            <img src="../../images/2.jpeg" style="width:160px;margin:0 0 10px 7px" />
            <img src="../../images/3.jpeg" style="width:160px;margin-bottom:10px" />
            <img src="../../images/4.jpeg" style="width:160px;margin:0 0 10px 7px" />
            <img src="../../images/5.jpeg" style="width:160px;margin-bottom:10px" />
            <img src="../../images/6.jpeg" style="width:160px;margin:0 0 10px 7px" />
          </el-col>
        </el-row>
      </div>
      <!-- 低价介绍板块 -->
      <div class="housingInformation">
        <el-row style=" border-bottom: 1px solid #ccc;height:35px;line-height:35px;">
            <h4>
            <el-col :span="9">价格来源</el-col>
            <el-col :span="9">低价房型</el-col>
            <el-col :span="6">最低价格/每晚</el-col>
            </h4>
        </el-row>
        <el-row style=" border-bottom: 1px solid #ccc;height:35px;line-height:35px">
            <i style="font-size:16px;color:#666">
            <el-col :span="9">携程</el-col>
            <el-col :span="9">高级大床房A</el-col>
            <el-col :span="6" ><i style="color:#ff9900">￥113</i>起</el-col>
            </i>
        </el-row>
        <el-row style=" border-bottom: 1px solid #ccc;height:35px;line-height:35px">
            <el-col :span="9">携程</el-col>
            <el-col :span="9">高级大床房A</el-col>
            <el-col :span="6"><i style="color:#ff9900">￥113</i>起</el-col>
        </el-row>
        <el-row style=" border-bottom: 1px solid #ccc;height:35px;line-height:35px">
            <el-col :span="9">携程</el-col>
            <el-col :span="9">高级大床房A</el-col>
            <el-col :span="6"><i style="color:#ff9900">￥113</i>起</el-col>
        </el-row>
      </div>
      <!-- 地图展示 -->
      <div class="map">
          <!-- 这里放地图组件 -->
          <hotelMap />
      </div>
      <!-- 住房基本信息 -->
      <div class="intake">
          <el-row style=" border-bottom: 1px solid #ccc;height:50px;line-height:50px;">
              <el-col :span="4">基本信息</el-col>
              <el-col :span="5">入住时间：14:00之后</el-col>
              <el-col :span="5">离店时间：12:00之后</el-col>
              <el-col :span="5">2010年开业 / 2015年装修</el-col>
              <el-col :span="5">酒店规模: 148间客房</el-col>
          </el-row>
          <el-row style=" border-bottom: 1px solid #ccc;height:50px;line-height:50px;">
              <el-col :span="4">主要设施</el-col>
              <el-col :span="20">
                  <el-tag type="info">外币兑换服务</el-tag>
                  <el-tag type="info">电梯</el-tag>
                  <el-tag type="info">洗衣服务</el-tag>
                  <el-tag type="info">热水壶</el-tag>
              </el-col>
          </el-row>
          <el-row style=" border-bottom: 1px solid #ccc;height:50px;line-height:50px;">
              <el-col :span="4">停车服务</el-col>
              <el-col :span="20">-</el-col>
          </el-row>
          <el-row style=" border-bottom: 1px solid #ccc;height:50px;line-height:50px;">
              <el-col :span="4">品牌信息</el-col>
              <el-col :span="20">-</el-col>
          </el-row>
      </div>
      <!-- 用户评论信息 -->
      <div class="userComment">
          <!-- 这里放用户评论信息 -->
          <userComment :data="userCommentMessage"/>
      </div>
    </div>
  </section>
</template>

<script>
import userComment from '@/components/hotel/userComment.vue'
import hotelMap from '@/components/hotel/hotelMap.vue'
export default {
    components:{
        userComment,
        hotelMap
    },
    props:{
        // data:[{type:Object,default:{}},]
        data:{}
    },
  data() {
    return {
      userCommentMessage:[]
    }
    
  },
  methods:{
       
    },
    mounted(){
        this.$axios({
            url:'/hotels/comments',
           
        }).then((res)=>{
            // console.log(res)
            this.userCommentMessage= res.data.data
            // console.log(this.userCommentMessage)
        })
        // console.log(this.data)
    }
};
</script>

<style lang="less" scoped>
.container {
  .title {
    padding: 20px 0;
  }
  .hotelMessage {
    margin-bottom: 30px;
    h4 {
      font-size: 22px;
    }
  }
  .showPicture {
    width: 1000px;
  }
  .housingInformation {
    cursor:pointer;
    el-row{
        height: 25px;
    }
  }
  .intake{
      margin:30px 0;
  }
  .userComment{}
}
</style>
