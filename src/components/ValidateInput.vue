<template>
  <h1></h1>
</template>

<script lang="ts">
import { defineComponent, reactive, PropType } from 'vue'
const emailReg = /^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
interface RuleProp {
  type: 'required' | 'email';
  message: string ;
}
export type RulesProp = RuleProp[]
export default defineComponent({
  setup () {
    return {

    }
  }
})
</script>

<style>

</style>
