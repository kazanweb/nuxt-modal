<template>
	<Modal :is-open="!!component" @close="handleModalClose">
		<component
			:is="component"
			@onClose="handleClose"
			v-bind="props"
		>
		</component>
	</Modal>
</template>

<script>
import Modal from "./Modal";
export default {
	components: {
		Modal
	},
	data() {
		return {
			component: null,
			props: null,
			closeOnClick: true
		}
	},
	methods: {
		handleModalClose(force = false) {
			if (!this.closeOnClick && !force) return;
			this.handleClose();
		},
		handleClose() {
			this.component = null;
		},
		handleKeyUp(e) {
			if (e.keyCode == 27) this.handleModalClose(true);
		}
	},
	mounted() {
		this.$nuxt.$on("modal-open", ({ component, props = null, closeOnClick = true }) => {
				this.component = component;
				this.props = props;
				this.closeOnClick = closeOnClick;
			}
		);
		this.$nuxt.$on('modal-close', () => {
			this.handleModalClose(true)
		});
		document.addEventListener("keyup", this.handleKeyUp);
	},
	beforeDestroy() {
		document.addEventListener("keyup", this.handleKeyUp);
	}
}
</script>
