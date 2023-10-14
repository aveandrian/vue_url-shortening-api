<script setup lang="ts">
import { ref } from 'vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faClose, faBars } from '@fortawesome/free-solid-svg-icons'

const isOpen = ref<boolean>(false)
function toggleIsOpen() {
  isOpen.value = !isOpen.value
}
</script>

<template>
  <nav>
    <img class="logo" src="/images/logo.svg" alt="Logo" />
    <div :class="`nav-items ${isOpen ? 'opened' : ''}`">
      <a>Features</a>
      <a>Pricing</a>
      <a>Resources</a>
      <div class="nav-items-divider"></div>
      <a class="login-btn">Login</a>
      <button class="signup-btn">Sign Up</button>
    </div>
    <FontAwesomeIcon
      :icon="isOpen ? faClose : faBars"
      class="menu-btn"
      @click="toggleIsOpen"
    />
  </nav>
</template>

<style>
nav {
  display: flex;
  align-items: center;
  height: 10vh;
  width: 100%;
  padding-inline: 10vw;
  margin-bottom: 10vh;
}

.menu-btn,
.nav-items-divider {
  display: none;
}

.logo {
  margin-right: 5vw;
}

.nav-items {
  font-weight: 700;
  width: 100%;
  display: flex;
  align-items: center;
  gap: 2vw;
}

.nav-items a {
  color: hsl(0, 0%, 75%);
}

.nav-items a:hover {
  cursor: pointer;
  color: hsl(255, 11%, 22%);
}

.login-btn {
  margin-left: auto;
}

.signup-btn {
  border: none;
  padding: 0.625rem 1.25rem;
  border-radius: 1.25rem;
  color: white;
  background-color: hsl(180, 66%, 49%);
}

.signup-btn:hover {
  cursor: pointer;
  background-color: #9be3df;
}

@media screen and (max-width: 60rem) {
  nav {
    padding-inline: 5vw;
    overflow: hidden;
  }
  .menu-btn,
  .nav-items-divider {
    display: block;
  }

  .menu-btn {
    margin-left: auto;
  }

  .nav-items-divider {
    height: 0.063rem;
    background-color: white;
    width: 100%;
  }

  .nav-items {
    z-index: 1;
    padding-block: 5vh;
    padding-inline: 5vw;
    border-radius: 0.625rem;
    position: absolute;
    top: 10vh;
    left: 5vw;
    width: 90vw;
    flex-direction: column;
    gap: 5vh;
    background: hsl(255, 11%, 22%);
    color: white;
    transform: translateX(120vw);
    transition: all 0.3s ease-in;
  }

  .nav-items.opened {
    transform: none;
  }

  .nav-items a {
    color: white;
  }

  .login-btn {
    margin: 0;
  }

  .signup-btn {
    width: 100%;
  }
}
</style>
