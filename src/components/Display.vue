<template>
  <!-- <div>Number of participants: {{ returnObject.noOfParticipants }}</div>
  <div>Max Price: {{ returnObject.maxPrice }}</div>
  <div>Type: {{ returnObject.typeRestriction }}</div>
  <div>Data: {{ data }}</div> -->
  <div class="displayData">
    <div class="keys">
      <div :class="[data[item] === null ? 'invisible' : '', 'key']" v-for="item in Object.keys(data)">{{ item }}</div>
    </div>
    <div class="values">
      <div :class="[item === null ? 'invisible' : '', 'value']" v-for="item in data">{{ item }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DisplayResult",
  props: {
    // returnObject: Object,
    data: Object,
  },
};
</script>

<style scoped>
.displayData {
  display: flex;
}
/* .displayData > * {
  flex: 0 0 50%;
} */
.keys {
  display: flex;
  flex-wrap: wrap;
  flex: 30%;
}
.values {
  display: flex;
  flex-wrap: wrap;
}
.key {
  background-color: #bfbf3f;
  width: 100%;
  border: 1px solid;
  height: 2em;
}
.value {
  border: 1px solid;
  border-color: #bfbf3f;
  width: 100%;
  height: 2em;
}
.invisible {
    /* background-color: blue; */
    display: none;
}
</style>