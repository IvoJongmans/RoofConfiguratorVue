<template>
  <div id="option_wall">
    <h5>Materiaal muur:</h5>
    <select v-model="data.selected" @change="emitMaterialChange">
      <option value="wood">Hout</option>
      <option value="stone">Baksteen</option>
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
        wood: {
          material_nl: "Hout",
          material_code: "wood",
          price: 100,
          image_url: 'wood.jpg',
          house_part: 'wall'
        },
        stone: {
          material_nl: "Steen",
          material_code: "stone",
          price: 150,
          image_url: 'stone.jpg',
          house_part: 'wall'
        }
      }
    };
  },

  methods: {
    emitMaterialChange() {
      var chosen_material = this.data.selected;
      EventBus.$emit("materialChange", this.data[`${chosen_material}`]);
    }
  }
};
</script>

<style>
#option_wall {
  grid-area: 2 / 1 / 3 / 2;
  text-align: center;
}
</style>
