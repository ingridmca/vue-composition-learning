<template>
  <div>
    <p>Spaces Left: {{ spacesLeft }} of {{ capacity }}</p>
    <div>Capacity: {{ capacity }}</div>
    <button @click="increaseCapacity()">Increase</button>
    <ul>
      <li v-for="(name, index) in attending" :key="index">
        {{ name }}
      </li>
    </ul>
  </div>
</template>

<script>
import { computed, reactive, toRefs } from "vue";
export default {
  setup() {
    const event = reactive({
      capacity: 1,
      attending: ["Tim", "Bob", "Joe"],

      spacesLeft: computed(() => {
        return event.capacity - event.attending.length;
      }),
    });

    const increaseCapacity = () => {
      event.capacity++;
    };

    return { ...toRefs(event), increaseCapacity };
  },
};
</script>
