<template>
    <div v-if="events.length">
      <ul v-for="(event, index) in events" :key="index" class="infoBox">
        <li>
          <span class="li-time">{{ event.eventDate}} / {{ event.eventTime }}</span><br>
          <span class="li-topic">{{ event.eventTitle }}</span><br>
          <span class="li-info">{{ event.eventInfo }}</span>
          <span hidden class="li-info">&nbsp;{{ event.eventCategory }}</span>
        </li>
      </ul>
    </div>
    <div v-else>
      <h2>No events currently listed.</h2>
    </div>
  </template>
  
  <script>
 
  import axios from 'axios';
  
  export default {

    data() {
      return {
        events: [],
      };
    },
    mounted() {
      this.fetchData();
      setInterval(() => {
        this.fetchData();
      }, 1800000);
    },
    methods: {
      fetchData() {
        axios
          .get(
            'https://docs.google.com/spreadsheets/d/e/2PACX-1vTGzcXLquYTzTma9c_Fj5Y0aJV0N_WgL9HpIPlqvQisneB-juhwtxTUNHSbYUqZv1NUc7i3w_KiacmO/pub?output=csv'
          )
          .then((response) => {
            const data = response.data
              .trim()
              .split('\n')
              .slice(1)
              .map((line) => {
                const [eventTime, eventDate, eventTitle, eventInfo, eventCategory] = line.split(',');
                if (eventInfo.includes('')) {
                  return { eventTime, eventDate, eventTitle, eventInfo, eventCategory };
                }
              })
              .filter((event) => event != null);
            this.events = data;
          })
          .catch((error) => {
            console.error(error);
          });
      },
    },
  };
  </script>
  
  <style>
  .infoBoxBs {
    background-color: #0F05A0;
    padding-left:25px;
  }
  .infoBox {
    width: 80%;
    margin: 0 auto;
    margin-top: 20px;
    width: 960px;
    height: 182px;
    background-color: #0f05a0;
    padding: 25px;
    text-decoration: none;
  }
  .li-time {
    font-family: 'Inter', sans-serif;
    font-size: 28px;
    font-weight: 900;
    color: #eb5e00;
    text-decoration: none;
  }
  .li-topic {
    font-family: 'Inter', sans-serif;
    font-size: 28px;
    font-weight: 900;
    color: #ffbfab;
    text-decoration: none;
  }
  .li-info {
    font-family: 'Inter', sans-serif;
    font-size: 28px;
    font-weight: 500;
    color: #ffbfab;
    text-decoration: none;
  }
  </style>