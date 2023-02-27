<template>
  <div>
    <div class="wrapper" @click="handlerWrapper" v-if="showWrapper()"></div>
    <v-card class="menu" :class="{ mobile: isMobile }" v-if="showMenu()">
      <div
        class="menu-container"
        v-for="item in lists"
        :key="item"
        @click="selectMenu(item.index)"
      >
        <p class="menu-text">
          {{ item.text }} {{ menuState }}
          <v-icon
            icon="mdi-triangle-small-up"
            v-if="showIcon(item.index)"
            class="menu-icon"
          ></v-icon>
        </p>
        <v-divider></v-divider>
      </div>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    state: Number,
    menuState: Boolean,
  },

  data() {
    return {
      isMobile: false,
      width: 0,
      lists: [
        {
          text: "content 1",
          index: 1,
        },
        {
          text: "content 2",
          index: 2,
        },
        {
          text: "content 3",
          index: 3,
        },
        {
          text: "content 4",
          index: 4,
        },
      ],
    };
  },

  created() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize();
  },

  methods: {
    showIcon(index) {
      if (index === this.state) return true;
      return false;
    },
    showMenu() {
      if (this.width > 960) return true;
      return this.menuState;
    },
    showWrapper() {
      if (this.width > 960) return false;
      return this.menuState;
    },

    selectMenu(index) {
      this.$emit("clickMenu", index);
      if (this.width < 960) {
        this.$emit("clickMenuIcon", true);
      }
    },
    // closeMenu() {
    //   this.$emit("clickMenuIcon", true);
    // },
    handlerWrapper() {
      this.$emit("clickMenuIcon", true);
    },

    handleResize() {
      this.width = window.innerWidth;
      if (this.width <= 960) {
        this.isMobile = true;
      } else {
        this.isMobile = false;
      }
    },
  },
};
</script>

<style scoped>
.menu {
  border: 1px solid rgba(0, 0, 0, 0.1);
  background-color: white;
  width: 360px;
  height: fit-content;
}
.menu-container {
  width: 100%;
  padding: 0 8px;
  transition: 0.2s;
}
.menu-container:hover {
  background: rgba(0, 0, 0, 0.05);
}

.menu-text {
  height: 72px;
  padding: 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.menu-icon {
  color: rgb(66, 78, 255);
  transform: rotate(270deg);
  font-size: 40px;
}

.mobile {
  position: absolute;
  z-index: 80;
  left: 50%;
  transform: translateX(-50%);
}
.wrapper {
  position: fixed;
  z-index: 80;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.1);
}
</style>
