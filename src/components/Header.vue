<template>
	<header>
		<router-link class="nav-link" id="logo" to="/">
			<TypedComponent></TypedComponent>
		</router-link>
		<div class="header-right">
			<router-link class="nav-link" to="/login">
				<span>Login</span>
			</router-link>
			<router-link class="nav-link" to="/signup">
				<span>Signup</span>
			</router-link>
		</div>
	</header>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TypedComponent from "@/components/Typed.vue";

export default defineComponent({
	name: "Header",
	components: {
		TypedComponent,
	},
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
/* Style the header with a grey background and some padding */
header {
	overflow: hidden;
	background-color: #333;
	padding: 20px 10px;
	color: white;
	a {
		float: left;
		color: white;
		text-align: center;
		padding: 12px;
		text-decoration: none;
		font-size: 18px;
		line-height: 25px;
		border-radius: 4px;
		:hover {
			background-color: #ddd;
			color: black;
		}
	}
	#logo {
		font-size: 25px;
		font-weight: bold;
	}
	.header-right {
		float: right;
	}
}
</style>
