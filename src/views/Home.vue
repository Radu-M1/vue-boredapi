<template>
  <!-- <div class="container"> -->
  <div class="card">
    <InputForm @update-display="updateDisplay" :types="types" />
    <Display :data="data" />
  </div>
  <!-- </div> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import InputForm from "../components/InputForm.vue";
import Display from "../components/Display.vue";
import axios from "axios";

export default {
  props: {
    activityList: Array,
  },
  data() {
    return {
      returnObject: {},
      data: {},
      types: [
        {
          id: "null",
          text: "NULL",
        },
        {
          id: "education",
          text: "Education",
        },
        {
          id: "recreational",
          text: "Recreational",
        },
        {
          id: "social",
          text: "Social",
        },
        {
          id: "diy",
          text: "DIY",
        },
        {
          id: "charity",
          text: "Charity",
        },
        {
          id: "cooking",
          text: "Cooking",
        },
        {
          id: "relaxation",
          text: "Relaxation",
        },
        {
          id: "music",
          text: "Music",
        },
        {
          id: "busywork",
          text: "Busywork",
        },
      ],
    };
  },
  name: "Home",
  components: {
    InputForm,
    Display,
  },
  methods: {
    async updateDisplay(returnObject) {
      // { this.noOfParticipants, this.maxPrice, this.type} = returnObject;
      // this.noOfParticipants = returnObject.noOfParticipants;
      // this.maxPrice = returnObject.maxPrice;
      // this.type = returnObject.type;
      this.returnObject = returnObject;
      const rawData = await axios({
        method: "get",
        baseURL: "https://www.boredapi.com/api/activity/",
        params: {
          participants: returnObject.noOfParticipants,
          type: returnObject.typeRestriction,
          maxprice: returnObject.maxPrice,
        },
      });
      this.data = rawData.data;
      // console.log("AICI!", this.data.data);
      this.data = Object.assign(this.data, this.returnObject);
      // console.log(this.activityList);
      this.$emit("add-to-list", this.data);
      // this.$emit("has-filters", this.returnObject);
    },
  },
};
</script>
