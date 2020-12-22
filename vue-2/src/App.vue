<!--
 * @Author: wangyz
 * @Date: 2020-12-18 10:05:07
 * @Description: file content
 * @LastEditors: wangyz
 * @LastEditTime: 2020-12-22 17:51:31
-->
<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <h2>欢迎光临</h2>
    <div>请选择</div>
  </div>
  <div>
    <button
      v-for="(item, index) in girls"
      v-bind:key="index"
      @click="selectGirlFun(index)"
    >
      {{ index }} : {{ item }}
    </button>
  </div>
  <div>你选择了【{{ selectGirl }}】为你服务</div>
</template>

<script lang="ts">
import { defineComponent, onBeforeMount, reactive, toRefs } from "vue";

export default defineComponent({
  name: "App",
  setup() {
    console.log("1-开始创建组件---------setup");
    interface DataProps {
      girls: string[];
      selectGirl: string;
      selectGirlFun: (index: number) => void;
    }
    const data: DataProps = reactive({
      girls: ["大脚", "刘英", "晓红"],
      selectGirl: "",
      selectGirlFun: (index: number) => {
        data.selectGirl = data.girls[index];
      }
    });
    onBeforeMount(() => {
      console.log("2-开始创建组件--------onBeforeMount");
    });
    const refData = toRefs(data);
    return {
      ...refData
    };
  },
  components: {}
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
