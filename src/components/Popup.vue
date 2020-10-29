<template>
<div class="popup">

</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

const Popup = defineComponent({
});

export default Popup
</script>

<style scoped lang="scss">
@import '@/common.scss';

.popup{
  width: 100%;
  position: absolute;
  top: rem(112);
  background-color: #fff;
  height: 50vh;
}
</style>
