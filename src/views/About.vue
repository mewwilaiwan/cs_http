<template>
  <div class="about">
    <!-- <h1>This is an about page</h1> -->
    <!-- <img src="../assets/live-streaming-thumbnail.jpg" height="200" width="1000"> -->
    <br>
    <ul class="list-group">
      <!-- <li class="list-group-item" v-for="(u,index) in users" :key="index">
        เรื่อง : {{u.headline}}
        <br>
        {{u.body}}{{u.img}} -->
      <!-- </li> -->
    </ul>
    <b-card-group deck id="p" class="list-group-item" v-for="(u,index) in users" :key="index">
      <b-card title="" header-tag="header" footer-tag="footer">
        <h6 slot="header" class="mb-0">{{u.headline}}</h6>
        <p class="card-text">{{u.body}}</p>
      </b-card>
    </b-card-group>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      users: []
    };
  },
  mounted() {
    axios
      .get("https://cs-http.firebaseio.com/data.json")
      .then(response => {
        console.log(response);
        const data = response.data;
        for (let key in data) {
          const user = data[key];
          user.id = key;
          this.users.push(user);
        }
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style>
#p {
  /* border: 1px solid red;  */
  margin: 35px;
}
</style>
