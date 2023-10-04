<template>
  <div v-if="isToggle" class="backdrop" @click="setToggle"></div>
  <aside :class="{ active: isToggle }">
    <div class="side-body">
      <div @click="setToggle" class="side-close">
        <img src="../assets/images/icon-close-menu.svg" alt="" />
      </div>

      <div class="side-wrapper">
        <ul>
          <li>
            <a @click="setFeature" href="#">
              <div class="link-icon">
                <span>feature</span>
                <img
                  :class="{ active: state.feature }"
                  src="../assets/images/icon-arrow-down.svg"
                  alt=""
                />
              </div>
            </a>
            <div :class="{ active: state.feature }" class="dropdown-list">
              <a class="dropdown-item" href="#">
                <div class="dropdown-icon">
                  <img src="../assets/images/icon-todo.svg" alt="" />
                </div>
                <span>todo list</span>
              </a>
              <a class="dropdown-item" href="#">
                <div class="dropdown-icon">
                  <img src="../assets/images/icon-calendar.svg" alt="" />
                </div>
                <span>caledar</span>
              </a>
              <a class="dropdown-item" href="#">
                <div class="dropdown-icon">
                  <img src="../assets/images/icon-reminders.svg" alt="" />
                </div>
                <span>reminders</span>
              </a>
              <a class="dropdown-item" href="#">
                <div class="dropdown-icon">
                  <img src="../assets/images/icon-planning.svg" alt="" />
                </div>
                <span>planning</span>
              </a>
            </div>
          </li>
          <li>
            <a @click="setCompany" href="#">
              <div class="link-icon">
                <span>company</span>
                <img
                  :class="{ active: state.company }"
                  src="../assets/images/icon-arrow-down.svg"
                  alt=""
                />
              </div>
            </a>
            <div :class="{ active: state.company }" class="dropdown-list">
              <a href="#" class="dropdown-item">
                <span>history</span>
              </a>
              <a href="#" class="dropdown-item">
                <span>history</span>
              </a>
              <a href="#" class="dropdown-item">
                <span>our team</span>
              </a>
              <a href="#" class="dropdown-item">
                <span>blog</span>
              </a>
            </div>
          </li>
          <li>
            <a href="#"> reminders </a>
          </li>
          <li>
            <a href="#"> planning </a>
          </li>
        </ul>
      </div>

      <div class="side-action">
        <button class="btn-main">login</button>
        <button class="btn-main btn-outlined">register</button>
      </div>
    </div>
  </aside>
</template>

<script>
import { computed, reactive } from "vue";

export default {
  props: ["toggle"],
  emits: ["on-close"],

  setup(props, { emit }) {
    const state = reactive({
      feature: false,
      company: false,
    });
    let isToggle = computed(() => props.toggle);

    function setToggle() {
      emit("on-close");
    }
    function setFeature() {
      state.feature = !state.feature;
    }
    function setCompany() {
      state.company = !state.company;
    }

    return {
      state,
      isToggle,

      setToggle,
      setCompany,
      setFeature,
    };
  },
};
</script>

<style scoped>
@import url("../assets/css/sidebar.css");
</style>
