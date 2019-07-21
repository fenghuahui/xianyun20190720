<template>
  <el-row>
    <!-- 左侧地图 -->
    <el-col :span="15">
      <div id="container" style="width:600px; height: 380px;margin:50px 0;"></div>
    </el-col>
    <!-- 右边导航栏 -->
    <el-col :span="9">
      <el-tabs v-model="activeName" @tab-click="handleClick" style="margin:40px 0; ">
        <el-tab-pane label="风景" name="first">
          <ul class="tabContents">
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
            <li>
              <span>高淳老街</span>
              <i>1.03公里</i>
            </li>
          </ul>
        </el-tab-pane>
        <el-tab-pane label="交通" name="second">
          <ul class="tabContent">
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
            <li>
              <span>甘霖路口(公交站)</span>
              <i>0.09公里</i>
            </li>
          </ul>
        </el-tab-pane>
      </el-tabs>
    </el-col>
  </el-row>
</template>

<script>
// import map from 'https://webapi.amap.com/maps?v=1.4.15&key=	430a1eebf34c91747e2ff1f3892770bc'
export default {
  mounted() {
    window.onLoad = function() {
      var map = new AMap.Map("container", {
        zoom: 11, //级别
        center: [116.39, 39.9], //中心点坐标
        viewMode: "3D" //使用3D模式
      });
      // 创建一个 Marker 实例：
      var marker1 = new AMap.Marker({
        position: new AMap.LngLat(116.59, 39.9), // 经纬度对象，也可以是经纬度构成的一维数组[116.39, 39.9]
        title: "北京"
      });
      var marker2 = new AMap.Marker({
        position: new AMap.LngLat(116.49, 39.91), // 经纬度对象，也可以是经纬度构成的一维数组[116.39, 39.9]
        title: "北京"
      });
      var marker3 = new AMap.Marker({
        position: new AMap.LngLat(116.39, 39.92),
        offset: new AMap.Pixel(-10, -10),
        icon: "//vdata.amap.com/icons/b18/1/2.png", // 添加 Icon 图标 URL// 经纬度对象，也可以是经纬度构成的一维数组[116.39, 39.9]
        title: "北京"
      });
      var markerList = [marker1, marker2, marker3];
      // 将创建的点标记添加到已有的地图实例：
      map.add(markerList);
    };
    var keys = "430a1eebf34c91747e2ff1f3892770bc";
    var url = `https://webapi.amap.com/maps?v=1.4.15&key=${keys}&callback=onLoad`;
    var jsapi = document.createElement("script");
    jsapi.charset = "utf-8";
    jsapi.src = url;
    document.head.appendChild(jsapi);
  },
  data() {
    return {
      activeName: "second"
    };
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event);
    }
  }
};
</script>
    
<style lang="less" scoped>
ul li {
  list-style: none;
}
*{
    padding: 0;
    margin: 0;
}
.tabContent {
  height: 339px;
  overflow-y: scroll;
  li {
    cursor: pointer;
    margin: 0 0 20px 0;
    span {
      //   padding-right: 160px;
    }
    i {
      float: right;
    }
  }
}
.tabContents {
  height: 339px;
  overflow-y: scroll;
  li {
    cursor: pointer;
    margin: 0 0 20px 0;
    span {
      //   padding-right: 180px;
    }
    i {
      float: right;
    }
  }
}
</style>

