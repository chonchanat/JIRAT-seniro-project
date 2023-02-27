<template>
  <div>
    <Navbar :menuState="menuState" @clickMenuIcon="clickMenuIcon" />
    <v-container class="container">
      <Menu
        :state="state"
        :menuState="menuState"
        @clickMenu="clickMenu"
        @clickMenuIcon="clickMenuIcon"
      />
      <Content :state="state" />
    </v-container>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Menu from "@/components/Menu.vue";
import Content from "@/components/Content.vue";
export default {
  components: {
    Navbar,
    Menu,
    Content,
  },

  data() {
    return {
      state: 1,
      menuState: false,
    };
  },

  methods: {
    clickMenu(index) {
      this.state = index;
    },
    clickMenuIcon() {
      this.menuState = !this.menuState;
    },
  },
};
</script>

<style scoped>
.container {
  margin-top: 80px;
  display: flex;
  position: relative;
}
</style>
