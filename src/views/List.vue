<template>
  <div class="list">
    <!-- <h1>This is an about page</h1> -->
    <button v-on:click="$emit('refresh-list')" class="btn btn-block refresh">
      Refresh List
    </button>
    <div class="table-row header">
      <div class="text" :class="item" v-for="item in Object.keys(dataDemo)">
        {{ item }}
      </div>
      <!-- <div class="text" :class="item" v-for="item in Object.keys(filters)">
        {{ item }}
      </div> -->
    </div>
    <div class="table-row" :key="data.key" v-for="data in activityList">
      <!-- {{ data.data }} -->
      <div class="text" v-for="item in data">{{ item }}</div>
    </div>
    <!-- <div>{{filters}}</div> -->
  </div>
</template>


<script>
export default {
  name: "List",
  props: {
    activityList: Array,
    // filters: Object,
  },
  created() {
    this.dataDemo = {
      activity: "Learn how to make a website",
      type: "education",
      participants: 1,
      price: 0.1,
      link: "",
      key: "9924423",
      accessibility: 0.3,
      maxParticipants: null, 
      maxPrice: null, 
      typeRestriction: null
    };
  },

  // emits: ["delete-task", "toggle-reminder"],
};
</script>

<style scoped>
/* @text-width: 180px;
@num-width: 80px; */
/* 180px: 180px;
80px: 80px; */

.table-row {
  display: flex;
  display: -webkit-flex;
  flex-direction: row;
  -webkit-flex-direction: row;
  flex-grow: 0;
  -webkit-flex-grow: 0;
  flex-wrap: wrap;
  -webkit-flex-wrap: wrap;
  width: 100%;
  padding-left: 15px;
  padding-right: 15px;
}

.text {
  /* flex-grow: 1;            -webkit-flex-grow: 1; */
  flex-grow: 1;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  padding-right: 20px;
}

.text {
  width: 120px;
}

.num {
  width: 80px;
}

body {
  font-size: 20px;
}

.table-row {
  border-bottom: 2px solid #e0e0e0;
  border-collapse: collapse;
  padding-top: 5px;
}

.table-row.header {
  background-color: rgb(221, 135, 43);
  font-weight: bold;
  padding-top: 8px;
  padding-bottom: 8px;
}

.refresh {
  margin-bottom: 1em;
}
/* .participants {
  width: 80px;
} */
.text:nth-of-type(1) {
  width: 400px;
}
.text:nth-of-type(2) {
  width: 120px;
}
.text:nth-of-type(5) {
  width: 100px;
}
/* .text:nth-of-type(8) {
  width: 150px;
} */

.text:nth-of-type(n+8) {
  color: blue;
}

.table-row:nth-of-type(2n+3) {
  background-color: rgb(255, 238, 219);
}

.selected {
  color: green;
}
</style>

