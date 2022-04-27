<template>
  <Header/>
	<div class="text-center">
		<router-view></router-view>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Header from '@/components/Header.vue'; // @ is an alias to /src

export default defineComponent({
  name: 'Home',
  components: {
    Header,
  },
});
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  color: white;
  background-color: #1e1e1e;
  width: 100vw;
  min-width: 600px;
}

.text-center {
  margin-top: 10vh;
}
</style>
