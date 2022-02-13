<template>

	<!-- Layout Header ( Navbar ) -->
	<a-layout-header>
		<div class="header-col header-btn">
			<a-button href="https://www.creative-tim.com/product/muse-vue-ant-design-dashboard" target="_blank" type="primary" shape="round">Sign In</a-button>
		</div>
	</a-layout-header>
	<!-- / Layout Header ( Navbar ) -->

</template>

<script setup lang="ts">
// Collapse navigation value.
// Binded model property for "Collapsible Navigation Menu" collapsed status .
const collapseNav= 0

</script>

<style lang="scss" scoped>

	.nav-link svg {
		margin-right: 5px;
		vertical-align: middle;
	}
	.nav-link span {
		vertical-align: middle;
	}
	.ant-menu-submenu-popup {
		width: 100%;
	}

</style>