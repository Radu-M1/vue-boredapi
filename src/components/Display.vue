<template>
  <h2 class="intro">Display Results:</h2>
  <div class="displayData">
    <div class="keys">
      <div
        :class="[
          data[item] === null ? 'invisible' : '',
          'key',
          ['maxParticipants', 'maxPrice', 'typeRestriction'].includes(item)
            ? 'restrictions'
            : '',
        ]"
        v-for="item in Object.keys(data)"
      >
        {{ item }}
      </div>
    </div>
    <div class="values">
      <div
        :class="[item === null ? 'invisible' : '', 'value']"
        v-for="item in data"
      >
        {{ item }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DisplayResult",
  props: {
    data: Object,
  },
};
</script>

<style scoped>
.displayData {
  display: flex;
}
.intro {
  margin-bottom: 1em;
}
.keys {
  display: flex;
  flex-wrap: wrap;
  flex: 30%;
}
.values {
  display: flex;
  flex-wrap: wrap;
  flex: 70%;
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
  display: none;
}

/* keeping .restrictions background color and color in case i want to display the query values for the result as well */

.restrictions {
  background-color: #3f7fbf;
  color: white;
  display: none;
}

.value:nth-of-type(n + 8) {
  display: none;
}
</style>