<template>
    <div class="sticky top-10 w-full">
        <div class="p-20 bg-pink-600 rounded shadow-md max-w-lg mx-auto my-0">
            <Typography tag="H5" color="text-neutral-50">{{message}}</Typography>
        </div>
    </div>
</template>

<script>
import Typography from '../typography/Typography';
export default {
	components: { Typography },
	props: {
		message: {
			type: String,
			default: ''
		}
	},
	setup() {
		return {};
	}
};
</script>

<style lang="scss" scoped>
</style>