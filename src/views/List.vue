<template>
  <div class="list">
    <!-- <h1>This is an about page</h1> -->
    <div :key="data.key" v-for="data in activityList">
      {{ data.data }}
    </div>
  </div>
</template>


<script>
export default {
  name: "List",
  props: {
    activityList: Array,
  },

  // emits: ["delete-task", "toggle-reminder"],
};
</script>

