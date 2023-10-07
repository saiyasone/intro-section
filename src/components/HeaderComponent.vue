<template>
  <header>
    <nav>
      <div class="nav-target">
        <div class="nav-brand">
          <a href="#">snap</a>
        </div>
        <ul>
          <li>
            <a id="feature-container" @click="setFeature" href="#"
              >feature
              <div class="link-icon">
                <img src="../assets/images/icon-arrow-down.svg" alt="" />
              </div>
            </a>
            <div :class="{ active: state.feature }" class="dropdown-list left">
              <div class="dropdown-item">
                <a href="#" class="dropdown-link">
                  <div class="dropdown-icon">
                    <img src="../assets/images/icon-todo.svg" alt="todo" />
                  </div>
                  <span>Todo List</span>
                </a>
              </div>
              <div class="dropdown-item">
                <a href="#" class="dropdown-link">
                  <div class="dropdown-icon">
                    <img src="../assets/images/icon-calendar.svg" alt="todo" />
                  </div>
                  <span>calendar</span>
                </a>
              </div>
              <div class="dropdown-item">
                <a href="#" class="dropdown-link">
                  <div class="dropdown-icon">
                    <img src="../assets/images/icon-reminders.svg" alt="todo" />
                  </div>
                  <span>reminders</span>
                </a>
              </div>
              <div class="dropdown-item">
                <a href="#" class="dropdown-link">
                  <div class="dropdown-icon">
                    <img src="../assets/images/icon-planning.svg" alt="todo" />
                  </div>
                  <span>Planning</span>
                </a>
              </div>
            </div>
          </li>

          <li>
            <a @click="setCompany" href="#"
              >company
              <div class="link-icon">
                <img src="../assets/images/icon-arrow-down.svg" alt="" />
              </div>
            </a>

            <div :class="{ active: state.company }" class="dropdown-list">
              <div class="dropdown-item">
                <a href="#" class="dropdown-link">
                  <span>history</span>
                </a>
              </div>
              <div class="dropdown-item">
                <a href="#" class="dropdown-link">
                  <span>our team</span>
                </a>
              </div>
              <div class="dropdown-item">
                <a href="#" class="dropdown-link">
                  <span>blog</span>
                </a>
              </div>
            </div>
          </li>
          <li>
            <a href="#">carents</a>
          </li>
          <li>
            <a href="#">about</a>
          </li>
        </ul>
      </div>
      <div class="nav-auth">
        <button class="btn-main">login</button>
        <button class="btn-main btn-outlined">register</button>
      </div>
      <div @click="setToggle" class="nav-mobile">
        <img src="../assets/images/icon-menu.svg" alt="" />
      </div>
    </nav>
  </header>
</template>

<style scoped>
@import url("../assets/css/header.css");
</style>

<script>
import { onMounted, reactive } from "vue";
export default {
  emits: ["on-close"],

  setup(_, { emit }) {
    const state = reactive({
      feature: false,
      company: false,
    });

    onMounted(() => {});

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
      setToggle,
      setFeature,
      setCompany,
    };
  },
};
</script>
