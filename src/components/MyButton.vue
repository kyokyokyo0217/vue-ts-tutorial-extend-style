<template>
  <button @click="onClick">
    <slot></slot>
  </button>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  props: {
    //シンプルなものはnative constructorでそのまま型推論
    greet: {
      type: String,
      required: true
    },
    count: {
      type: Number,
      required: true
    }
  },

  methods: {
    onClick() {
      this.$emit("clicked");
    }
  }
});
</script>
