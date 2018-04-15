<template>
  <div class="loginPage">
    <br/>
    <br/>
    <br/>
    <el-form label-width="80px" label-position='left'>
      <el-form-item label="User">
        <el-input type="text" id="user" v-model="formName.user" @blur="inputBlur('user',formName.user)"></el-input>
              <p>{{formName.userError}}</p>
      </el-form-item>
      <el-form-item label="Password">
        <el-input type="password" id="password" v-model="formName.password" @blur="inputBlur('password',formName.password)"></el-input>
              <p>{{formName.passwordError}}</p>
      </el-form-item>
      <el-button type="primary" @click="submitForm('formName')" v-bind:disabled="formName.beDisabled">Submit</el-button>
      <el-button type="danger" @click="resetForm">Reset</el-button>
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
      formName: {// param in form
        user: '',
        userError: '',
        password: '',
        passwordError: '',
        beDisabled: true
      },
      beShow: false// Pass to parent
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
      // Communicate with parent
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
          this.formName.userError = 'UserName could not be empty'
        } else {
          this.formName.userError = ''
        }
      } else if (errorItem === 'password') {
        if (inputContent === '') {
          this.formName.passwordError = 'Password could not be empty'
        } else {
          this.formName.passwordError = ''
        }
      }
      // Update button status
      if (this.formName.user !== '' && this.formName.password !== '') {
        this.formName.beDisabled = false
      } else {
        this.formName.beDisabled = true
      }
    }
  }
}
</script>

<style scoped>
h1 {
  font-weight: normal;
  text-align: center;
}

.loginPage {
  width: 40%;
  display: inline-block;
}
</style>
