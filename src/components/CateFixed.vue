<template>
  <el-row >
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-s-goods"></i>Clothing & Shoes</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-delete-solid"></i>Entertainment</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-s-tools"></i>Music</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-phone-outline"></i>Pets</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-warning"></i>Kitchen Accessories</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-video-camera-solid"></i>Travel Equipments</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-message-solid"></i>Growing & Garden</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-s-platform"></i>Electrical Tools</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-s-custom"></i>Mother Care</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-s-comment"></i>Toys & Entertainment</div></el-col>
    <el-col :span="6"><div class="grid-content bg-purple"><i class="el-icon-s-finance"></i>Vintage</div></el-col>
  </el-row>
</template>

<script>
export default {};
</script>

<style scoped>
  i {
    position: absolute;
    top : 0px;
    
  }
  .el-row {
    margin-bottom: 20px;
    display: flex;
    justify-content: center;
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    margin-right: 3px;
    color: gray;
  }
  .bg-purple:hover {
    background: #d3dce6;
    color: rgb(63, 63, 231)
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 50px;
    width: 150px;
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
</style>