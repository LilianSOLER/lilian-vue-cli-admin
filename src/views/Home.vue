<template>
	<section>
		<div class="home">
      <p>{{ text }}</p>
    </div>
	</section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

interface DataComponent {
  text: string;
}

export default defineComponent({
	name: "Home",
  data(): DataComponent {
    return {
      text: "Bonjour",
    };
  },

});
</script>

<style scoped lang="scss"></style>
