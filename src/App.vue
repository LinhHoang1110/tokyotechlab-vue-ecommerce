<template>
  <div id="app">
    <CateFixed />
    <el-container>
      <el-aside>
        <SideBar />
      </el-aside>
      <el-main>
        <MainContent />
      </el-main>
    </el-container>
  </div>
</template>

<script>
import CateFixed from "./components/CateFixed";
import SideBar from "./components/SideBar";
import MainContent from "./components/MainContent";

export default {
  name: "App",
  components: {
    CateFixed,
    SideBar,
    MainContent,
  },
};
</script>

<style scoped>
.el-aside {
  text-align: center;
  line-height: 50px;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}

.el-container {
  margin: 0 150px;
}
</style>
