<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label for="maxParticipants">Number of participants</label>
      <input
        type="number"
        v-model="maxParticipants"
        name="maxParticipants"
        id="maxParticipants"
        placeholder="None"
        required
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
        required
      />
    </div>
    <div class="form-control">
      <div>
        <label for="type">Type</label>
        <select v-model="typeRestriction" required>
          <option value="" selected disabled>--Please, select a type--</option>
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
      maxParticipants: null,
      maxPrice: null,
      typeRestriction: null,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      const returnObject = {
        maxParticipants: this.maxParticipants,
        maxPrice: this.maxPrice,
        typeRestriction: this.typeRestriction,
      };
      if (
        (this.maxParticipants < 1 && this.maxParticipants) ||
        this.maxParticipants === 0
      ) {
        return alert(
          "Please, introduce a number of participants between [1, n]"
        );
      }
      if ((this.maxPrice < 0 || this.maxPrice > 1) && this.maxPrice) {
        return alert("Please, enter a maximum price between [0,1]");
      }
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
select {
  margin: auto;
  width: 100%;
}
input {
  margin: auto;
  width: 100%;
}
</style>