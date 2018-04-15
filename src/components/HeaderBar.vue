<template>
    <div>
        <el-row type="flex" class="row-bg" justify="center" align="middle" :gutter="10">
            <el-col :span="2">
                <div class="grid-content">
                    <img src="../assets/ghost_50.png">
                </div>
            </el-col>
            <el-col :span="8">
                <div class="grid-content">
                    <h1>{{ msg }}</h1>
                </div>
            </el-col>
            <el-col :span="2">
                <div class="grid-content bg-purple">
                    <router-link to="/">Home</router-link>
                </div>
            </el-col>
            <el-col :span="2">
                <div class="grid-content bg-purple">
                    <router-link to="/login">Login</router-link>
                </div>
            </el-col>
            <el-col :span="2">
                <div class="grid-content bg-purple">
                    <router-link to="/coins/ethereum">Ethereum</router-link>
                </div>
            </el-col>
            <el-col :span="2">
                <div class="grid-content bg-purple">
                    <router-link to="/coins/bitcoin">Bitcoin</router-link>
                </div>
            </el-col>
        </el-row>
    </div>

</template>

<script>
export default {
  name: 'HeaderBar',
  data () {
    return {
      msg: 'Welcome to CoinDrama'
    }
  }
}
</script>

<style scoped>
h1 {
  font-weight: normal;
  text-align: left;
}
.el-row {
    margin-bottom: 1px;
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 2px 0;
    background-color: #f9fafc;
  }
</style>
