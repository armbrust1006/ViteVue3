<script setup lang="ts">
import { reactive, ref } from 'vue';

defineProps<{ msg: string }>();

const count = ref(1);

/* 
  ref == reactive 두 API는 같음! <-- 비슷하지만 자료형에 따라 사용법이 다름
  ref 는 기본형을 사용할 때 이용
  ractive 는 참조형을 사용할 때 이용
  무조건 변수에 지정 안하면 사용 못함
*/
// ref 를 참조형으로 사용도 가능함. 하지만 '.value'를 통해서 처리하게 됨!
const state = ref({
  list : ['00', '01', '02']
});

const updateState = () => {
  state.value.list = ['10', '11'];
};
/*
// 작동 안함!!!
const updateState = () => {
  state.list = ['10', '11'];
};
*/

// 작동 안함!!!
const name = reactive('front');


</script>

<template>
  <h1>{{ msg }}</h1>

  <div>
    <!-- 정상 작동 -->
    <a v-for="(a,i) in state.list" :key="i">{{ a }}</a>
    <!-- 작동 안됨 -->
    <a v-for="(a,i) in list" :key="i">{{ a }}</a>
    <button @click="updateState">click</button>
  </div>

  <p>
    Recommended IDE setup:
    <a href="https://code.visualstudio.com/" target="_blank">VSCode</a>
    +
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
  </p>

  <p>See <code>README.md</code> for more information.</p>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Docs
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Docs</a>
  </p>

  <button type="button" @click="count++">count is: {{ count }}</button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
