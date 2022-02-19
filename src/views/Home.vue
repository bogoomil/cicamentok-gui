<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <br />
    <button v-on:click="testGet()">Test GET</button>
    <button v-on:click="testPublicGet()">Test PUBLIC GET</button>
    <button v-on:click="testPost()">Test POST</button>
    <button v-on:click="whoami()">WHOAMI</button>
    <button v-on:click="login()">Login</button>
    <button v-on:click="logout()">Logout</button>

    <div id="result">{{ msg }}</div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import axios from "axios";

@Options({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {
  msg = "Zerge";

  public created(): void {
    console.log("created");
  }

  private testGet() {
    axios
      .get("/api/private/get?id=zerge")
      .then(function (response) {
        // handle success
        alert(response);
      })
      .catch(function (error) {
        // handle error
        alert(error);
      })
      .then(function () {
        // always executed
      });
  }

  private testPost() {
    axios
      .post("/api/private/save", { id: "qwertz", name: "zerge name" })
      .then(function (response) {
        // handle success
        console.log(response);
      })
      .catch(function (error) {
        // handle error
        alert(error);
      })
      .then(function () {
        // always executed
      });
  }

  private testPublicGet() {
    axios
      .get("/api/public/get?id=zerge")
      .then(function (response) {
        // handle success
        alert(response);
      })
      .catch(function (error) {
        // handle error
        alert(error);
      })
      .then(function () {
        // always executed
      });
  }

  private whoami() {
    axios
      .get("/auth/whoami")
      .then(function (response) {
        // handle success
        alert(response);
      })
      .catch(function (error) {
        // handle error
        alert(error);
      })
      .then(function () {
        // always executed
      });
  }

  private login() {
    window.location.href = "/oauth2/authorization/cicamentok";
  }

  private logout() {
    window.location.href = "/logout";
  }
}
</script>
