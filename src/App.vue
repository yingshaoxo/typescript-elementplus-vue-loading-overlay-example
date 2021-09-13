<template>
  <div>
    <el-card class="box-card">
      <el-button class="button" type="text" @click="handleClick"
        >Click Me</el-button
      >

      <Loading
        v-model:active="dict.isLoading"
        :can-cancel="true"
        :is-full-page="false"
      >
        <template v-slot:default>
          <div>This won't cover the card!!!!!!!!</div>
        </template>
      </Loading>

      <template #header>
        <div class="card-header">
          <span>Card name</span>
        </div>
      </template>
      <div v-for="o in 4" :key="o" class="text item">
        {{ "List item " + o }}
      </div>
    </el-card>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";

import Loading from "vue-loading-overlay";
import "vue-loading-overlay/dist/vue-loading.css";

export default defineComponent({
  name: "App",
  components: {
    Loading,
  },
  setup: (props) => {
    const dict = reactive({
      isLoading: false,
    });

    const handleClick = () => {
      dict.isLoading = true;

      setTimeout(() => {
        dict.isLoading = false;
      }, 5000);
    };

    return {
      dict,

      handleClick,
    };
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
