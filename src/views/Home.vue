<template>
  <div class="card">
    <InputForm @update-display="updateDisplay" :types="types" />
    <Display :data="data" />
  </div>
</template>

<script>
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
      this.returnObject = returnObject;
      const rawData = await axios({
        method: "get",
        baseURL: "https://www.boredapi.com/api/activity/",
        params: {
          participants: returnObject.maxParticipants,
          type: returnObject.typeRestriction,
          maxprice: returnObject.maxPrice,
          // minPrice: returnObject.minPrice,
          // price: returnObject.searchPrice,
          // key: returnObject.searchKey,
          // minaccessibility: returnObject.minAccessibility,
          // maxaccessibility: returnObject.maxaccessibility,
        },
      });
      if (Object.keys(rawData.data).includes("error")) {
        return alert(rawData.data.error);
      }
      this.data = rawData.data;
      this.data = Object.assign(this.data, this.returnObject);
      this.$emit("add-to-list", this.data);
    },
  },
};
</script>
