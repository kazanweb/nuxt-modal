<template>
	<div>
		{{ title }}
		<button @click="onClose">close</button>
	</div>
</template>

<script>
export default {
	props: {
		title: {
			type: String,
			default: ''
		},
	},
	methods: {
		onClose() {
			this.$nuxt.$emit("modal-close")
		}
	},
}
</script>
