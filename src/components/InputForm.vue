<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label for="noOfParticipants">Number of participants</label>
      <input
        type="number"
        v-model="noOfParticipants"
        name="noOfParticipants"
        id="noOfParticipants"
        placeholder="None"
      />
    </div>
    <div class="form-control">
      <label for="maxPrice">Max Price</label>
      <input
        type="number"
        v-model="maxPrice"
        name="maxPrice"
        id="maxPrice"
        placeholder="0"
        step="any"
      />
    </div>
    <div class="form-control">
      <div>
        <label for="type">Type</label>
        <select v-model="typeRestriction">
          <option v-for="item in types" :value="item.id">
            {{ item.text }}
          </option>
        </select>
      </div>
    </div>
    <input type="submit" value="Submit" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "InputForm",
  props: {
    types: Array,
  },
  data() {
    return {
      noOfParticipants: null,
      maxPrice: null,
      typeRestriction: null,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      const returnObject = {
        noOfParticipants: this.noOfParticipants,
        maxPrice: this.maxPrice,
        typeRestriction: this.typeRestriction,
      };
      this.$emit("updateDisplay", returnObject);
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>