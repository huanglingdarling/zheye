<template>
  <div class="container">
    <global-header :user="user"></global-header>
    <column-list :list="list"></column-list>

    <form>
      <div class="mb-3">
        <label class="form-label">邮箱</label>
        <validate-input :rules="emailRules" v-model="emailVal" placeholder="请输入" type="text"></validate-input>
      </div>
      <div class="mb-3">
        <label class="form-label">密码</label>
        <validate-input
          :rules="passwordRules"
          v-model="passwordVal"
          placeholder="请输入"
          type="password"
        ></validate-input>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import 'bootstrap/dist/css/bootstrap.min.css';
import ColumnList from './components/ColumnList.vue';
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue';
import ValidateInput from '@/components/ValidateInput.vue';
import { RulesProp } from './interface/RulesProp';
import { testData } from './mock/testData';
const currentUser: UserProps = {
  isLogin: true,
  name: 'darling'
};

export default defineComponent({
  name: 'App',
  components: { ColumnList, GlobalHeader, ValidateInput },
  setup() {
    const emailVal = ref('darling');
    const emailRules: RulesProp = [
      { type: 'required', message: '电子邮箱不能为空' },
      { type: 'email', message: '电子邮箱格式不正确' }
    ];
    const passwordVal = ref('');
    const passwordRules: RulesProp = [
      { type: 'required', message: '密码不能为空' },
      { type: 'password', message: '请输入数字和字母组合的8-16位密码' }
    ];

    return {
      list: testData,
      user: currentUser,
      emailRules,
      emailVal,
      passwordVal,
      passwordRules
    };
  }
});
</script>

<style></style>
