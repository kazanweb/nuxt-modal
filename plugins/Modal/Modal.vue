<template>
	<div class="modal"
	     :class="{ active: isOpen }"
	     @click="$emit('close')">
		<div class="section" :class="{open: isOpen}" @click.stop>
			<div class="close" @click="$emit('close', true)"></div>
			<slot></slot>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		isOpen: Boolean
	}
}
</script>

<style scoped src="./Modal.css"></style>
