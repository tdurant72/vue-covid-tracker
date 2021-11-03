<template>
    <button
        class="w-auto text-base transition duration-300 ease-in-out border-2 px-4 py-2  shadow-sm rounded-md mx-4 my-2 h-auto transform hover:shadow-lg  hover:-translate-y-px"
        :class="btnClasses"
    >
        <slot></slot>
    </button>
</template>

<script>
export default {
	props: {
		bg: {
			type: String,
			default: 'bg-primary-500'
		},
		bgh: {
			type: String,
			default: 'bg-transparent'
		},
		txt: {
			type: String,
			default: 'text-primary-50'
		},
		bd: {
			type: String,
			default: 'border-transparent'
		}
	},
	computed: {
		btnClasses() {
			return `${this.bg} ${this.txt} ${this.bd} hover:${this.bgh}`;
		}
	}
};
</script>

<style lang="scss" scoped>
</style>