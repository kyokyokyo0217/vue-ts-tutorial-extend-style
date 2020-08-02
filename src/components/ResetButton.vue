<template>
  <button @click="onClick">Reset</button>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  methods: {
    onClick() {
      this.$emit("clicked");
    }
  }
});
</script>
