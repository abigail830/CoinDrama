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
            <el-col :span="8">
                <div class="grid-content">
                    <el-menu :default-active="$route.path" router class="el-menu-demo" mode="horizontal" @select="handleSelect">
                        <el-menu-item index="/">Home</el-menu-item>
                        <el-menu-item index="/login">Login</el-menu-item>
                        <el-menu-item index="/coins/ethereum">Ethereum</el-menu-item>
                        <el-menu-item index="/coins/bitcoin">Bitcoin</el-menu-item>
                    </el-menu>
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
      activeIndex: '/',
      msg: 'Welcome to CoinDrama'
    }
  },
  methods: {
    handleSelect (key, keyPath) {
      console.log(key, keyPath)
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
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 1px 0;
  }
</style>
