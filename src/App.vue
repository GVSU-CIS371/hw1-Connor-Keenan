<template>
  <div>
    <Beverage 
      :isIced="currentTemp === 'Cold'" 
      :selectedBase="currentBase"
      :selectedCreamer="currentCreamer"
      :selectedSyrup="currentSyrup"
    />
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
      
      <li>
        <template v-for="base in bases" :key="base">
          <label>
            <input
              type="radio"
              name="baseBeverage"
              :id="`b${base}`"
              :value="base"
              v-model="currentBase"
            />
            {{ base }}
          </label>
        </template>
      </li>
      
      <li>
        <template v-for="creamer in creamers" :key="creamer">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`c${creamer}`"
              :value="creamer"
              v-model="currentCreamer"
            />
            {{ creamer }}
          </label>
        </template>
      </li>
      
      <li>
        <template v-for="syrup in syrups" :key="syrup">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`s${syrup}`"
              :value="syrup"
              v-model="currentSyrup"
            />
            {{ syrup }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import { temps, currentTemp } from "./stores/beverage";
import { ref } from 'vue';

// Define new options for question 1
const bases = ["Coffee", "Green Tea", "Black Tea"];
const currentBase = ref("Coffee");

const creamers = ["No Creamer", "Milk", "Cream", "Half & Half"];
const currentCreamer = ref("No Creamer");

const syrups = ["No Syrup", "Vanilla", "Caramel", "Hazelnut"];
const currentSyrup = ref("No Syrup");
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
