<template>
	<div>
		<Nuxt />
		<ModalRoot />
	</div>
</template>
<script>
import ModalRoot from "../plugins/Modal/ModalRoot";
export default {
	components: {ModalRoot}
}
</script>
