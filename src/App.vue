<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <!-- <column-list :list="list"></column-list> -->
    <form>
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">邮箱地址</label>
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          v-model="emailRef.val"
          @blur="validateEmail"
        >
        <div calss="form-text" v-if="emailRef.error">{{emailRef.message}}</div>
      </div>
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">密码</label>
        <input type="password" class="form-control" id="exampleInputPassword1">
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'
// import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
import 'bootstrap/dist/css/bootstrap.min.css'
// const testData: ColumnProps[] = [
//   {
//     id: 1,
//     title: 'test1的专栏',
//     description: '这是的test1专栏，有一段非常有意思的简介，可以更新一下欧',
//     avatar: 'http://vue-maker.oss-cn-hangzhou.aliyuncs.com/vue-marker/5ee22dd58b3c4520912b9470.jpg?x-oss-process=image/resize,m_pad,h_100,w_100'
//   },
//   {
//     id: 2,
//     title: 'test2的专栏',
//     description: '这是的test2专栏，有一段非常有意思的简介，可以更新一下欧',
//     avatar: 'http://vue-maker.oss-cn-hangzhou.aliyuncs.com/vue-marker/5ee22dd58b3c4520912b9470.jpg?x-oss-process=image/resize,m_pad,h_100,w_100'
//   },
//   {
//     id: 1,
//     title: 'test1的专栏',
//     description: '这是的test1专栏，有一段非常有意思的简介，可以更新一下欧',
//     avatar: 'http://vue-maker.oss-cn-hangzhou.aliyuncs.com/vue-marker/5ee22dd58b3c4520912b9470.jpg?x-oss-process=image/resize,m_pad,h_100,w_100'
//   },
//   {
//     id: 2,
//     title: 'test2的专栏',
//     description: '这是的test2专栏，有一段非常有意思的简介，可以更新一下欧'
//   }
// ]
const emailReg = /^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
const currentUser: UserProps = {
  isLogin: true,
  name: 'huangling'
}
export default defineComponent({
  name: 'App',
  components: {
    // ColumnList,
    GlobalHeader
  },
  setup () {
    const emailRef = reactive({
      val: '',
      error: false,
      message: ''
    })
    const validateEmail = () => {
      if (emailRef.val.trim() === '') {
        emailRef.error = true
        emailRef.message = '邮箱不能为空'
      } else if (!emailReg.test(emailRef.val)) {
        emailRef.error = true
        emailRef.message = '邮箱格式不正确'
      }
    }
    return {

      // list: testData,
      currentUser,
      emailRef,
      validateEmail
    }
  }
})
</script>

<style>
</style>
