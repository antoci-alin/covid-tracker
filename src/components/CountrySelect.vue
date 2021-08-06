<template>
  <select
    v-model="selected"
    class="form-select mt-1 block w-full border p-3 rounded mt-10"
    @change="onChange"
  >
    <option value="0">Select Country</option>
    <option
      v-for="country in countries"
      :value="country.ID"
      :key="country.ID"
      >{{ country.Country }}</option
    >
  </select>
</template>

<script>
export default {
  name: 'Countryselect',
  props: ['countries'],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);

      this.$emit('get-country', country);
    },
  },
};
</script>
