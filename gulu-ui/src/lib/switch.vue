<template>
  <div>
    <button @click="toggle" :class="{ checked: value }"><span></span></button>
    <div>{{ value }}</div>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";
export default {
  props: {
    value: Boolean,
  },
  setup(props,context) {
    const toggle = () => {
      context.emit('update:value',!props.value)
    };
    return { toggle };
  },
};
</script>

<style lang="scss" scoped>
$h: 22px;
$h2: $h - 4px;
button {
  height: $h;
  width: $h * 2;
  border: none;
  background: #bfbfbf;
  border-radius: $h/2;
  position: relative;
}
span {
  position: absolute;
  top: 2px;
  left: 2px;
  height: $h2;
  width: $h2;
  background: white;
  border-radius: $h2 / 2;
  transition: left 250ms;
}
button.checked {
  background: #1890ff;
}
button.checked > span {
  left: calc(100% - #{$h2} - 2px);
}
button:focus {
  outline: none;
}
button:active{
    > span { width: $h2 + 4px; }
}
button.checked:active {
  > span { width: $h2 + 4px; margin-left: -4px; }
}
</style>
