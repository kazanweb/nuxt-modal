<!-- Please remove this file from your project -->
<template>
  <div class="relative flex items-top justify-center min-h-screen bg-gray-100 sm:items-center sm:pt-0">
	    <div @click="onClick">show popup</div>
  </div>
</template>

<script>
export default {
	methods: {
		onClick() {
			import("../components/Title").then((Title) => {
					this.$nuxt.$emit("modal-open", {
						component: Title.default,
						props: {
							title: "my component's property"
						},
					});
				}
			);
		}
	}
}
</script>
