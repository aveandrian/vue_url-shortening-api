<template>
  <div class="suggested-link">
    <p class="link-full-url">
      {{ fullLink }}
    </p>
    <div class="suggested-link-divider"></div>
    <div class="short-link-wrapper">
      <p class="link-short-url">{{ shortLink }}</p>
      <button :class="`copy-btn ${isCopied ? 'copied' : ''}`" @click="copy">
        {{ isCopied ? 'Copied!' : 'Copy' }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps<{
  shortLink: string
  fullLink: string
}>()
const isCopied = ref<boolean>(false)
function copy() {
  navigator.clipboard.writeText(props.shortLink)
  isCopied.value = true
}
</script>

<style>
.suggested-link {
  padding: 0.938rem;
  padding-inline: 1.875rem;
  border-radius: 0.625rem;
  display: flex;
  align-items: center;
  gap: 1vw;
  background-color: white;
}

.suggested-link-divider {
  display: none;
}

.link-full-url {
  width: 100%;
  margin-right: auto;
  text-overflow: ellipsis;
  overflow: hidden;
  text-align: left;
}

.short-link-wrapper {
  display: flex;
  align-items: center;
  gap: 1vw;
}

.copy-btn {
  padding-block: 0.625rem;
  padding-inline: 1.875rem;
  border-radius: 0.313rem;
  border: none;
  background: #2bd1d1;
  color: white;
  font-weight: 700;
}

.link-short-url {
  color: #2bd1d1;
}

.copy-btn.copied {
  color: white;
  background-color: #3b2f55;
}

.copy-btn:hover {
  cursor: pointer;
  background-color: #9be3df;
}

.copy-btn.copied:hover {
  color: white;
  background-color: #3b2f55;
}

@media screen and (max-width: 60rem) {
  .suggested-link {
    flex-direction: column;
    align-items: start;
    justify-content: center;
    text-align: start;
    padding: 0;
    width: 100%;
  }

  .link-full-url,
  .short-link-wrapper {
    padding-block: 0.938rem;
    padding-inline: 1.875rem;
  }

  .short-link-wrapper {
    width: 100%;
    display: flex;
    align-items: start;
    flex-direction: column;
    gap: 1vh;
  }

  .copy-btn {
    width: 100%;
  }

  .suggested-link-divider {
    display: block;
    width: 100%;
    height: 0.063rem;
    background-color: hsl(0, 0%, 75%);
  }
}
</style>
