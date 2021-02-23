<template>
  <div id="map">
    <div id="container">
      <el-amap vid="amapDemo" :events="events"> </el-amap>
    </div>
    <button @click="get">click</button>
  </div>
</template>

<script>
export default {
  data: (vm) => ({
    map: null,
    events: {
      init: (o) => {
        vm.map = o;
      },
    },
  }),
  mounted() {
    console.log(this.map, "map");
  },
  methods: {
    get() {
      var path = [
        [116.403322, 39.920255],
        [116.410703, 39.897555],
        [116.402292, 39.892353],
        [116.389846, 39.891365],
      ];

      var polygon = new AMap.Polygon({
        path: path,
        strokeColor: "#FF33FF",
        strokeWeight: 6,
        strokeOpacity: 0.2,
        fillOpacity: 0.4,
        fillColor: "#1791fc",
        zIndex: 50,
      });

      this.map.add(polygon);
      // 缩放地图到合适的视野级别
      this.map.setFitView([polygon]);
    },
  },
};
</script>

<style scoped>
#container {
  width: 700px;
  height: 580px;
  border: 1px solid red;
}
</style>