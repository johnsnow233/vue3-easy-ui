<template>
  <div class="topnav">
    <div class="logo">LOGO</div>
    
    <div class="menu">
      <div>菜单1</div>
      <div>菜单2</div>
    </div>
    <span  class="toggleAside" @click="toggleAside">
  </span>
  </div>
</template>
<style lang="scss" scoped>
$color: #007974;
.topnav {
  background: pink;
  color: $color;
  display: flex;
  padding: 16px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 20;
  justify-content: center;
  align-items: center;
  >.logo {
    max-width: 6em;
    margin-right: auto;
    >svg {
      width: 32px;
      height: 32px;
    }
  }
  >.menu {
    display: flex;
    white-space: nowrap;
    flex-wrap: nowrap;
    >li {
      margin: 0 1em;
    }
  }
  >.toggleAside {
    width: 32px;
    height: 32px;
    position: absolute;
    left: 16px;
    top: 50%;
    transform: translateY(-50%);
    display: none;
    background: fade-out(black, 0.9);
  }
  @media (max-width: 500px) {
    >.menu {
      display: none;
    }
    >.logo {
      margin: 0 auto;
    }
    >.toggleAside {
      display: inline-block;
    }
  }
}
</style>
<script lang="ts">
import { inject, Ref } from 'vue'
export default {
    setup() {
        const asideVisible = inject<Ref<boolean>>('xxx')
        console.log(asideVisible)
        const toggleAside =()=>{
            
            asideVisible.value = !asideVisible.value
            console.log(asideVisible.value)
        }
        return {toggleAside}
        
    },
}
</script>
