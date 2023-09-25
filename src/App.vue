<script>
import Wheel from "./components/Wheel.vue";
export default {
  components:{Wheel}
}
</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-header>
        <h2>金多多吃什么</h2>
      </el-header>
      <el-main>
        <Wheel></Wheel>
      </el-main>
    </el-container>
  </div>
</template>


<style scoped>
</style>
