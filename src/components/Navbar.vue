<template>
  <div class="navbar-container bg-white">
    <div class="container">
      <nav class="navbar d-flex">
        <div class="d-flex center-v">
          <router-link to="/">
            <Icon style="height: 50px;" name="delizioso-logo"/>
          </router-link>
        </div>
        <ul class="navbar-wrapper">
          <li class="navbar-item d-flex center-v" style="position: relative;">
            <div class="d-flex">
              <router-link to="/">
                <span class="test">Home</span>
              </router-link>
            </div>
            <div
              v-bind:class="(currentRouteName === 'Home')?'navbar-item-marker active':'navbar-item-marker'"
            ></div>
          </li>
          <li class="navbar-item d-flex center-v">
            <router-link to="/gallery">
              <span class="test">F'Gallery</span>
            </router-link>
            <div
              v-bind:class="(currentRouteName === 'Gallery')?'navbar-item-marker active':'navbar-item-marker'"
            ></div>
          </li>
        </ul>
        <ul class="navbar-wrapper right" style="margin-left: auto;">
          <li class="navbar-item d-flex center-v" style="position: relative;">
            <div class="d-flex">
              <router-link to="/cart">
                <button
                  class="button no-hover d-flex center-v bg-transparent"
                  style="position: relative;"
                  to="/cart"
                >
                  <Icon name="cart-icon" style="height: 18px;"/>
                  <div
                    v-bind:class="(store.state.popped)?'badges popped':'badges'"
                    v-if="store.state.items.length !== 0"
                  >{{store.state.items.length || null}}</div>
                </button>
              </router-link>
              <div
                class="d-flex center-v bg-primary"
                style="height: 40px; width: 40px; border-radius: 50%; margin-left: 0.5rem; pointer: cursor;"
              >
                <Icon name="user-icon" style="height: 18px;"/>
              </div>
            </div>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
import Icon from "@/components/Icon";
import { inject } from "vue";
export default {
  name: "Navbar",
  setup() {
    const store = inject("store");
    return {
      store
    };
  },
  components: {
    Icon
  },
  computed: {
    currentRouteName() {
      return this.$route.name;
    }
  }
};
</script>
