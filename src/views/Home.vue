<template>
  <div class="home">
    <p>{{ greetText }}</p>
    <p>Total Greeting: {{ count }}</p>
    <p v-if="isVip">You're VIP User!!</p>
    <p>
      <my-button :greet="greetText" :count="count" @clicked="onMyButtonClicked">Greet</my-button>
    </p>
    <p>
      <reset-button @clicked="onResetButtonClicked"></reset-button>
    </p>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

export type DataType = {
  count: number;
  greetText: string;
};

export default Vue.extend({
  components: {
    MyButton,
    ResetButton
  },

  data(): DataType {
    return {
      count: 0,
      greetText: "Hello!"
    };
  },

  computed: {
    isVip(): boolean {
      return this.count >= 5;
    }
  },

  //lifecycle hooks
  created(): void {
    console.log("created");
  },

  watch: {
    count(c: number) {
      if (c === 5) {
        alert("Congratulations! Now You're VIP!");
      }
    }
  },

  methods: {
    onMyButtonClicked(): void {
      this.greetText = "Hello Again!!";
      this.count++;
    },
    onResetButtonClicked(): void {
      this.count = 0;
      this.greetText = "Hello!!";
    }
  }
});
</script>
