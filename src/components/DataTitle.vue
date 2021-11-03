<template>
    <div class="text-center mb-8">
        <Typography tag="H2" color="text-secondary-500" weight="font-bold">{{text}}</Typography>
        <Typography tag="H5" class="mt-4 mb-10">{{timestamp}}</Typography>
    </div>
</template>

<script>
import dayjs from 'dayjs';
import Typography from '@/components/typography/Typography';

import { computed } from 'vue';
export default {
	name: 'DataTitle',
	components: { Typography },
	props: ['text', 'dataDate'],
	setup({ dataDate }) {
		return {
			timestamp: computed(() =>
				dayjs(dataDate).format('MMMM D YYYY, h:mm:ss a')
			)
		};
	}
};
</script>

<style lang="scss" scoped>
</style>