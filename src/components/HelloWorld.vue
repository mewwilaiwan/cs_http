<template>
  <div class="About">
    <!-- <h1>{{ msg }}</h1> -->
    <!-- <h1>{{httpdata}}</h1> -->
    <div>
      <b-container>
        <b-card-group>
          <b-col deck v-for="(m, index) in photos" :key="index" cols="4" class="pad">
            <b-card
            v-bind:title="m.albumId"
              v-bind:img-src="m.id"
              img-alt="Image"
              img-top
              tag="article"
              style="max-width: 20rem; "
              @ok="handleOk"
              
            >
              <b-button href="#" variant="primary">Go somewhere</b-button>
            </b-card>
          </b-col>
        </b-card-group>
      </b-container>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      httpdata: "",
      photos: {
        albumId: "",
        id: "",
        url: "",
        thumbnailUrl: ""
      }
    };
  },
  mounted() {
    axios({
      method: "GET",
      url: "http://jsonplaceholder.typicode.com/photos"
    }).then(result => {
      // console.log(result);
      this.httpdata = result.data;
    });
  },
  methods: {
    submit() {
      console.log(this.news);
      let uri = "https://cs-http.firebaseio.com/data.json";
      axios.post(uri, this.news).then(response => {
        console.log(response);
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
