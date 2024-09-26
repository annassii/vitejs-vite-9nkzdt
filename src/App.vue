<template>
  <div @click="showRadialMenu" class="menu-area">
    <div
      v-if="isMenuVisible"
      class="radial-menu"
      :style="{ top: menuTop + 'px', left: menuLeft + 'px' }"
    >
      <div class="menu-option" id="option1">1</div>
      <div class="menu-option" id="option2">2</div>
      <div class="menu-option" id="option3">3</div>
      <div class="menu-option" id="option4">4</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isMenuVisible: false, // Controls the visibility of the menu
      menuLeft: 0, // X-coordinate of the menu
      menuTop: 0, // Y-coordinate of the menu
    };
  },
  methods: {
    showRadialMenu(event) {
      // Toggle menu visibility
      this.isMenuVisible = !this.menuVisible;

      // Set the menu position based on the click event
      this.menuLeft = event.clientX - 50; // Adjust to center
      this.menuTop = event.clientY - 50; // Adjust to center

      console.log('Menu at X: ' + this.menuLeft + ', Y: ' + this.menuTop);
    },
  },
};
</script>

<style scoped>
.menu-area {
  width: 100vw;
  height: 100vh;
  position: relative;
  overflow: hidden;
}

.radial-menu {
  position: absolute;
  width: 100px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  background-color: rgba(0, 0, 0, 0.8);
}

.menu-option {
  position: absolute;
  width: 40px;
  height: 40px;
  background-color: red;
  border: 2px solid white;
  border-radius: 50%;
  color: white;
  text-align: center;
  line-height: 40px;
}

/* Positioning options to create the pizza shape */
#option1 {
  top: 0;
  left: 50%;
  transform: translateX(-50%);
}

#option2 {
  top: 50%;
  left: 0;
  transform: translateY(-50%);
}

#option3 {
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}

#option4 {
  top: 50%;
  right: 0;
  transform: translateY(-50%);
}
</style>
