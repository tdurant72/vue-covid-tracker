<template>
    <div class="border-2 border-neutral-300 p-2 rounded">
        <div class="p-4 rounded bg-green-600 cursor-pointer" @click="isOpen = !isOpen">
            <Typography tag="H5" color="text-neutral-50" weight='font-bold'>{{title}}</Typography>
        </div>
        <div class="mt-4 border-2 border-neutral-300 p-2 rounded" :class="isOpen?'d-block':'hidden'">
            <slot></slot>
        </div>

    </div>
</template>

<script>
import Typography from './typography/Typography';
import { ref } from 'vue';
export default {
	name: 'Accordion',
	components: { Typography },
	props: {
		title: {
			type: String,
			default: 'Accordion'
		}
	},
	setup() {
		const isOpen = ref(false);
		return {
			isOpen
		};
	}
};
</script>

<style lang="scss" scoped>
</style>