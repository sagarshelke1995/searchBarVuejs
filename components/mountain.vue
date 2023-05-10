<template>
    <div>
    <!-- /////////////////////// -->
    <div class="max-w-xl mx-auto">
        <div class="py-2 text-gray-500">fetching title from "https://api.nuxtjs.dev/mountains"</div>
            <input v-model="searchText" @input="searchData"
             type="text" placeholder="search here" class="border-2 border-blue-200 w-full px-2 py-2 outline-none rounded-md">
            <div class="grid grid-cols-2 pt-5">
                <div class="border-[1px] p-2">Titale</div>
                <div class="border-[1px] p-2">Country</div>
            </div>
            <div class="a">
                <div class="a" v-for="(item, index) in searchResults" :key="item.title">
                    <div class="grid grid-cols-2">
                        <div class="border-[1px] p-2">{{ item.title }} </div>
                        <div class="border-[1px] p-2">{{ item.countries[0] }}</div>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        searchText: '',
        searchResults: [],
      };
    },
    methods: {
      searchData() {
        if (this.searchText.length > 0) {
          axios
            .get('https://api.nuxtjs.dev/mountains')
            .then(response => {
              const filteredData = response.data.filter(item => {
                return item.title.toLowerCase().includes(this.searchText.toLowerCase());
              });
              this.searchResults = filteredData;
            })
            .catch(error => {
              console.error('Error fetching data:', error);
            });
        } else {
          this.searchResults = [];
        }
      },
    },
  };
  </script>