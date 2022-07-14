<template>
  <div>
    <select id="country"
            @change="changeCountry($event)"
    >
      <option value="0">Все страны</option>
      <option value="1">Россия</option>
      <option value="2">Англия</option>
      <option value="3">Америка</option>
    </select>
    <!--Регионы-->
    <select id="region"
            @change="changeRegion($event)"
    >
      <option v-for="(region, i) in selectedRegion"
              :key="i"
              :value="region.regionId"
      >
        {{region.title}}
      </option>
    </select>
    <!--Города-->
    <select id="city">
      <option v-for="(city, i) in selectedCity"
              :key="i"
              :value="city.regionId">
        {{city.title}}
      </option>
    </select>
  </div>
</template>

<script>
    export default {
        name: 'App',

        data() {
            return {
                //    ---------ОПИСАНИЕ ЗАДАЧИ----------
                // Подключить vue.js 3 версии и сделать загрузку зависимых списков.
                // Например, Выбрали страну Россию -> в 2 select подгрузились регионы России -> выбрали регион -> в 3 select подгрузились города выбранного региона.
                selectedRegion: [],
                selectedCity: [],
                regions: [
                    {
                        'title': 'Московская обл.',
                        'countryId': 1,
                        'regionId': 1,
                    },
                    {
                        'title': 'Краснодарский край.',
                        'countryId': 1,
                        'regionId': 2,
                    },

                    {
                        'title': 'Западный Мидленд',
                        'countryId': 2,
                        'regionId': 3,
                    },
                    {
                        'title': 'Восточный Мидленд',
                        'countryId': 2,
                        'regionId': 4,
                    },

                    {
                        'title': 'Айдахо',
                        'countryId': 3,
                        'regionId': 5,
                    },
                    {
                        'title': 'Алабама',
                        'countryId': 3,
                        'regionId': 6,
                    },
                ],

                cities: [
                    {
                        'title': 'Видное',
                        'regionId': 1
                    },
                    {
                        'title': 'Краснодар',
                        'regionId': 2
                    },

                    {
                        'title': 'Бирмингем',
                        'regionId': 3
                    },
                    {
                        'title': 'Ноттингем',
                        'regionId': 4
                    },

                    {
                        'title': 'Айдахо-Фолс',
                        'regionId': 5
                    },
                    {
                        'title': 'Монтгомери',
                        'regionId': 6
                    },
                ]
            }
        },

        methods: {
            changeCountry(val) {
                this.selectedRegion = this.regions.filter(item => item.countryId === +val.target.value);
                this.selectedCity = this.cities.filter(item => item.regionId === this.selectedRegion[0]?.regionId);
            },

            changeRegion(val) {
                this.selectedCity = this.cities.filter(item => item.regionId === +val.target.value);
            }
        }
    }
</script>

<style>
</style>
