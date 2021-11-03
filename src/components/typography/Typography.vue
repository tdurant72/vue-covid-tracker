<template>
	<component :is="tagType" :class="[typeClasses, switchClasses]">	
		<slot></slot>
	</component>
</template>

<script>
export default {
	name: 'Typography',
	props: {
		color: {
			type: String,
			default: 'text-neutral-800'
		},
		weight: {
			type: String,
			default: 'font-normal'
		},
		tag: {
			type: String,
			default: 'P'
		}
	},
	computed: {
		typeClasses() {
			return `${this.color} ${this.weight}`;
		},
		tagType() {
			return `${this.tag}`;
		},
		switchClasses() {
			if (this.tagType == 'H1')
				return 'text-5xl md:text-6xl lg:text-7xl 2xl:text-8xl';
			if (this.tagType == 'H2') return 'text-3xl md:text-4xl lg:text-5xl';
			if (this.tagType == 'H3') return 'text-2xl lg:text-3xl';
			if (this.tagType == 'H4') return 'text-xl lg:text-2xl';
			if (this.tagType == 'H5') return 'text-lg lg:text-xl';
			if (this.tagType == 'Caption') return 'text-sm lg:text-base';
			if (this.tagType == 'P') return 'text-base lg:text-lg';
			return 'text-base lg:text-lg';
		}
	}
};
</script>

<style lang="scss" scoped>
</style>
