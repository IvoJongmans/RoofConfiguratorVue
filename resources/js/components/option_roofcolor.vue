<template>
  <div id="option_roof">
    <h5>Dakkleur:</h5>
    <select v-model="data.selected" @change="emitColorChange">
      <option value="red">Rood</option>
      <option value="grey">Grijs</option>
    </select>
  </div>
</template>

<script>
import { EventBus } from "../event-bus.js";

export default {
  data() {
    return {
      data: {
        selected: "",
        red: {
          color_nl: "Rood",
          color_code: "red",
          price: 20,
          house_part: 'roof'
        },
        grey: {
          color_nl: "Grijs",
          color_code: "grey",
          price: 50,
          house_part: 'roof'
        }
      }
    };
  },

  methods: {
    emitColorChange() {
      var chosen_color = this.data.selected;
      EventBus.$emit("colorChange", this.data[`${chosen_color}`]);
    }
  }
};
</script>

<style>
#option_roof {
  grid-area: 1 / 1 / 2 / 2;
  text-align: center;
}
</style>
