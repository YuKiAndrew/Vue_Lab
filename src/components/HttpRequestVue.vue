<template>
  <div id="fetchMethod">
    <p>fetch data</p>
    <button @click="fetchData">Fetch Data</button>
    <p v-if="data">{{data}}</p>
    <p>fetch json</p>
    <button @click="fetchJsonFile">Fetch Json</button>
    <p v-if="dataJson">{{dataJson}}</p>
  </div>
  <br/>
  <div id="obtainInformationFromAPI">
    <h1>API</h1>
    <p>Click the button to fetch data with an HTTP request.</p>
    <p>Each click generates an object with a random user from <a href="https://random-data-api.com/" target="_blank">https://random-data-api.com/</a>.</p>
    <button @click="fetchDataFromAPI">Fetch API data</button>
    <pre v-if="APIData">{{APIData}}</pre>
    <div v-if="APIData" id="showAPIData">
      <img :src="APIData.avatar" alt="avatar">
      <pre>{{APIData.first_name + " " + APIData.last_name}}</pre>
      <p>{{APIData.employment.title}}</p>
    </div>
  </div>
  <div id="visitAPIviaAxios">
    <h1>Example</h1>
    <p>Click the button to fetch data with an HTTP request.</p>
    <p>Each click generates an object with a random user from <a href="https://random-data-api.com/" target="_blank">https://random-data-api.com/</a>.</p>
    <p>The robot avatars are lovingly delivered by <a href="http://Robohash.org" target="_blank">RoboHash</a>.</p>
    <button @click="fetchAxiosData">Axios Data Fetch</button>
    <div v-if="axiosData" id="dataDiv">
      <img :src="axiosData.data.avatar" alt="avatar">
      <pre>{{ axiosData.data.first_name + " " + axiosData.data.last_name }}</pre>
      <p>"{{ axiosData.data.employment.title }}"</p>
    </div>
  </div>
</template>

<script>
import axios  from "axios";

export default {
  data() {
    return {
      data: null,
      dataJson: null,
      APIData: null,
      axiosData: null
    }
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('/files/data.txt');
        this.data = await response.text();
      } catch (error) {
        console.error('Error fetching this file', error)
      }
    },
    async fetchJsonFile() {
      try {
        const response = await fetch('/files/file.json');
        this.dataJson = await response.json();
      } catch (error) {
        console.error('Error fetching this file', error)
      }
    },
    async fetchDataFromAPI() {
      try {
        const response = await fetch("https://random-data-api.com/api/v2/users");
        this.APIData = await response.json()
      } catch (error) {
        console.error('Error fetching this API', error)
      }
    },
    async fetchAxiosData() {
      try {
        this.axiosData = await axios.get("https://random-data-api.com/api/v2/users");
      } catch (error) {
        console.error('Error fetching this API', error)
      }
    }
  }
}
</script>

<style>
#dataDiv {
  width: 240px;
  background-color: aquamarine;
  border: solid black 1px;
  margin-top: 10px;
  padding: 10px;
}
#dataDiv > img {
  width: 100%;
}
pre {
  font-size: larger;
  font-weight: bold;
}
</style>