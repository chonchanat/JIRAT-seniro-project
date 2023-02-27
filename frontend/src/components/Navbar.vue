<template>
  <div class="navbar">
    <div class="navbar-header">
      <v-icon icon="mdi-vpn"></v-icon>
      <p class="navbar-header-text">AIM-senior project</p>
    </div>
    <v-icon icon="mdi-menu" v-if="isMobile" @click="clickMenuIcon"></v-icon>
  </div>
</template>

<script>
export default {
  props: {
    menuState: Boolean,
  },

  data() {
    return {
      isMobile: false,
    };
  },
  created() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize();
  },
  methods: {
    handleResize() {
      this.width = window.innerWidth;
      if (this.width <= 960) {
        this.isMobile = true;
      } else {
        this.isMobile = false;
      }
    },

    clickMenuIcon() {
      this.$emit("clickMenuIcon", true)
    }
  },
};
</script>

<style scoped>
.navbar {
  height: 60px;
  padding: 0 24px;
  box-shadow: 0 2px 8px gray;
  background-color: white;
  display: flex;
  align-items: center;
  position: fixed;
  justify-content: space-between;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
}
.navbar-header {
  display: flex;
  align-items: center;
}
.navbar-header-text {
  font-size: 20px;
  margin-left: 8px;
  font-weight: bold;
}
</style>
