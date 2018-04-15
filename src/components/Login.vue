<template>
  <div class="loginPage">
    <h1>登录</h1>
      <el-form>
        <el-form-item label="user">
          <el-input type="text" id="user" v-model="formName.user" @blur="inputBlur('user',formName.user)"></el-input>
                <p>{{formName.userError}}</p>
            </el-form-item>
            <el-form-item label="password">
                <el-input type="password" id="password" v-model="formName.password" @blur="inputBlur('password',formName.password)"></el-input>
                <p>{{formName.passwordError}}</p>
            </el-form-item>
            <el-button type="primary" @click="submitForm('formName')" v-bind:disabled="formName.beDisabled">提交</el-button>
            <el-button @click="resetForm">重置</el-button>
        </el-form>
  </div>
</template>

<script>
import Axios from 'axios'
import HeaderBar from '@/components/HeaderBar'

export default {
  name: '',
  data () {
    return {
      formName: {// 表单中的参数
        user: '',
        userError: '',
        password: '',
        passwordError: '',
        beDisabled: true
      },
      beShow: false// 传值给父组件
    }
  },

  components: {
    HeaderBar
  },
  /* props:[
        'fromParent'
    ], */
  methods: {
    resetForm: function () {
      this.formName.user = ''
      this.formName.userError = ''
      this.formName.password = ''
      this.formName.passwordError = ''
    },
    submitForm: function (formName) {
      // 与父组件通信传值
      // this.$emit('showState', [this.beShow,this.formName.user])
      // 提交user password
      var user
      var password
      user = this.formName.user
      password = this.formName.password
      console.log(user, password)
      Axios.get('../../src/php/login.php?user=' + user + '&password=' + password)
        .then(function (res) {
          console.log(res)
        })
        .catch(function () {
        })
    },
    inputBlur: function (errorItem, inputContent) {
      if (errorItem === 'user') {
        if (inputContent === '') {
          this.formName.userError = '用户名不能为空'
        } else {
          this.formName.userError = ''
        }
      } else if (errorItem === 'password') {
        if (inputContent === '') {
          this.formName.passwordError = '密码不能为空'
        } else {
          this.formName.passwordError = ''
        }
      }
      // 对于按钮的状态进行修改
      if (this.formName.user !== '' && this.formName.password !== '') {
        this.formName.beDisabled = false
      } else {
        this.formName.beDisabled = true
      }
    }
  }
}
</script>

<style>
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
