<template>
  <section v-if="showToast === true">
    <Toast :message="toastMessage"/>
  </section>
  <main v-if="!loading">
    <DataTitle :dataDate="dataDate" :text="title" />

    <DataBoxes :stats="status" />

    <CountrySelect :countries="countries" @get-country="getCountryData" />

    <Button v-if="countrySelected"  @click="clearCountryData" bg="bg-green-700" bgh="bg-green-600">Clear Country</Button>

  </main>

  <main v-else class="flex flex-col align-center justify-center text-center">
    <Typography tag="H2" weight="font-bold" class="mt-10 mb-6">
      Fetching Data
    </Typography>
    <img :src="require('../assets/hourglass.gif')" alt="" class="w-24 m-auto" />
  </main>
</template>

<script>
import axios from 'axios';
import CountrySelect from '@/components/CountrySelect';
import DataBoxes from '@/components/DataBoxes';
import DataTitle from '@/components/DataTitle';
import Button from '@/components/UI/Button';

import Typography from '@/components/typography/Typography';

import Toast from '@/components/UI/Toast';
import { ref } from 'vue';
export default {
	name: 'Home',
	components: {
		DataTitle,
		DataBoxes,
		CountrySelect,
		Button,
		Typography,

		Toast
	},
	setup() {
		const loading = ref(true);
		const errors = ref(false);
		const title = ref('Global');
		const dataDate = ref('');
		const toastMessage = ref('');
		const status = ref({});
		const countries = ref([]);
		const countrySelected = ref(false);
		const showToast = ref(false);

		const triggerToast = () => {
			showToast.value = true;
			setTimeout(() => (showToast.value = false), 5000);
		};
		const fetchCovidData = async () => {
			try {
				const res = await axios.get('https://api.covid19api.com/summary');
				// console.log('res', res);
				return await res.data;
			} catch (error) {
				console.log('Error:', error);
				toastMessage.value = error;
				errors.value = true;
				triggerToast();
			}
		};
		const getCountryData = country => {
			status.value = country;
			title.value = country.Country;
			countrySelected.value = true;
			console.log('countrySelected', countrySelected.value);
		};
		const clearCountryData = async () => {
			loading.value = true;
			const data = await fetchCovidData();
			title.value = 'Global';
			status.value = data.Global;
			loading.value = false;
			countrySelected.value = false;
		};
		const baseSetup = async () => {
			const data = await fetchCovidData();
			dataDate.value = data.Date;
			status.value = data.Global;
			countries.value = data.Countries;
			loading.value = false;
		};
		baseSetup();
		return {
			loading,
			title,
			dataDate,
			status,
			countries,
			getCountryData,
			clearCountryData,
			countrySelected,
			errors,
			triggerToast,
			showToast,
			toastMessage
		};
	}
};
</script>

