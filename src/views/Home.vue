<template>
  <div class="home">
    <PartTime/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import PartTime from "@/components/index.vue"; // @ is an alias to /src

@Options({
  components: {
    PartTime
  }
})
export default class Home extends Vue {}
</script>
