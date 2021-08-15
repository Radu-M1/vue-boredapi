<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/list">List</router-link>
  </div>
  <div class="container">
    <router-view
      @add-to-list="addToList"
      @refresh-list="refreshList"
      :activityList="activityList"
    ></router-view>
  </div>
</template>

<script>
// import { reactive } from "@vue/reactivity";
export default {
  data() {
    return {
      activityList: [],
    };
  },
  name: "App",
  methods: {
    addToList(data) {
      this.activityList.push(data);
      // console.log(this.activityList);
      // const activityList = reactive(this.activityList)
      // persistent = this.activityList
      // this.persistent.push(data)
      // console.log(this.persistent)
      // this.activityList = this.persistent;
      // localStorage.setItem('activity-list', JSON.stringify(this.activityList))
    },
    refreshList() {
      this.activityList = [];
    }
  },
  // created() {
  //   this.persistent = reactive([])
  // }
  mounted() {
    console.log("App Mounted");
    if (localStorage.getItem("activity-list")) {
      this.activityList = JSON.parse(localStorage.getItem("activity-list"));
    }
  },
  watch: {
    activityList: {
      handler() {
        // console.log("Activity List array changed!");
        localStorage.setItem(
          "activity-list",
          JSON.stringify(this.activityList)
        );
      },
      deep: true,
    },
  },
};
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
  font-size: 1em;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.container {
  display: flex;
  justify-content: center;
}

.card {
  max-width: 700px;
  margin: 30px 30px auto 30px;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  /* min-width: 700px; */
}

.list {
  /* max-width: 700px; */
  margin: 30px 30px auto 30px;
  overflow: auto;
  min-height: 300px;
  /* border: 1px solid steelblue; */
  padding: 30px;
  border-radius: 5px;
  min-width: 700px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: auto;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  /* width: 50%; */
  width: 10em;
}
</style>
