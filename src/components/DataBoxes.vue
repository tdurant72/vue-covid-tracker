<template>
    <div class="grid md:grid-cols-2 gap-4">
        <div class="shadow-md bg-primary-100 p-10 text-center rounded">
            <Typography tag="H4" color="text-primary-900" weight="font-bold" class="mb-4">Cases</Typography>
            <div class="mb-4 flex justify-center">
                <Typography weight="font-bold">New: </Typography>
                <Typography > {{numberWithCommas(stats.NewConfirmed)}}</Typography>
            </div>
            <div class="mb-4 flex justify-center">
                <Typography tag="H5" weight="font-bold">Total: </Typography>
                <Typography  tag="H5"> {{numberWithCommas(stats.TotalConfirmed)}}</Typography>
            </div>
        </div>
        <div class="shadow-md bg-primary-200 p-10 text-center rounded">
            <Typography tag="H4" color="text-primary-900" weight="font-bold" class="mb-4">Deaths</Typography>
            <div class="mb-4 flex justify-center">
                <Typography tag="H5" weight="font-bold">New: </Typography>
                <Typography  tag="H5"> {{numberWithCommas(stats.NewDeaths)}}</Typography>
            </div>
            <div class="mb-4 flex justify-center">
                <Typography tag="H5" weight="font-bold">Total: </Typography>
                <Typography tag="H5"> {{numberWithCommas(stats.TotalDeaths)}}</Typography>
            </div>
        </div>
    </div>
</template>

<script>
import Typography from '@/components/typography/Typography';

export default {
	name: 'DataBoxes',
	props: ['stats'],
	components: { Typography },
	setup() {
		return {
			numberWithCommas(x) {
				return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
			}
		};
	}
};
</script>

<style lang="scss" scoped>
</style>