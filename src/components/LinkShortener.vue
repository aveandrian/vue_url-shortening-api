<template>
  <div class="link-shortener-container">
    <div class="link-shortner-wrapper">
      <form @submit.prevent="handleSubmit" class="link-shortener-form">
        <input
          :class="`link-input ${error ? 'input-error' : ''}`"
          type="text"
          placeholder="Shorten a link here..."
          :value="linkInput"
          @input="handleChange"
        />
        <input class="shorten-btn" type="submit" value="Shorten it!" />
      </form>
      <p v-if="error" class="error">{{ error }}</p>
    </div>
    <template v-if="shortLinksList.length"> </template>
    <SuggestedLink
      v-for="shortLinkListItem in shortLinksList"
      :key="shortLinkListItem.id"
      :="shortLinkListItem"
    />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { nanoid } from 'nanoid'
import axios from 'axios'
import SuggestedLink from './SuggestedLink.vue'

const TOKEN = 'jyIhoMzE4jvhhmlnaOgrs2jRTRGf4yoraYeRlHDhaoRRpDtWi8YGX6WlEKz7'

const linkInput = ref<string>('')
const error = ref<string | unknown>()
const shortLinksList = ref<Array<any>>([])

function handleChange(event: Event) {
  linkInput.value = (event.target as HTMLInputElement).value
  error.value = null
}

async function handleSubmit() {
  if (linkInput.value == '' || !isValidURL(linkInput.value))
    return (error.value = 'Please add a valid link')

  try {
    const { data } = await axios.post(
      `https://api.tinyurl.com/create?api_token=${TOKEN}`,
      {
        url: linkInput.value
      }
    )
    shortLinksList.value = [
      ...shortLinksList.value,
      {
        id: nanoid(),
        fullLink: linkInput.value,
        shortLink: data.data.tiny_url
      }
    ]
  } catch (err) {
    error.value = err
  }
  linkInput.value = ''
}

function isValidURL(str: string) {
  var httpRegex =
    /^https?:\/\/(?:www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b(?:[-a-zA-Z0-9()@:%_\+.~#?&\/=]*)$/
  if (httpRegex.test(str)) {
    return true
  } else {
    return false
  }
}
</script>

<style>
.link-shortener-container {
  width: 100%;
  transform: translateY(-7vh);
  display: flex;
  flex-direction: column;
  gap: 2vh;
}

.link-shortner-wrapper {
  width: 100%;
  padding-block: 4vh;
  padding-inline: 5vw;
  background: url('/images/bg-shorten-desktop.svg'), #3a3053;
  border-radius: 0.625rem;
}

.link-shortener-form {
  display: flex;
  align-items: center;
  gap: 1vw;
}

.link-input {
  height: 3.75rem;
  padding-inline: 0.8rem;
  border-radius: 0.625rem;
  flex: 1;
}

.link-input.input-error {
  border: 0.188rem solid hsl(0, 87%, 67%);
}

.link-input:focus {
  outline: none;
}

.shorten-btn {
  height: 3.75rem;
  padding-inline: 2rem;
  border-radius: 0.625rem;
  border: none;
  background: #2bd1d1;
  color: white;
  font-weight: 700;
  font-size: 1.2rem;
  letter-spacing: 0.05em;
}

.shorten-btn:hover {
  cursor: pointer;
  background-color: #9be3df;
}

.error {
  margin-top: 0.625rem;
  font-style: italic;
  color: hsl(0, 87%, 67%);
}

@media screen and (max-width: 60rem) {
  .link-shortner-wrapper {
    background: url('/images/bg-shorten-mobile.svg'), #3a3053;
    background-repeat: no-repeat;
    background-position: 100% 0;
  }
  .link-shortener-form {
    flex-direction: column;
    gap: 2vh;
    height: fit-content;
  }

  .link-input {
    width: 100%;
    padding-block: 2vh;
    padding-inline: 5vw;
  }

  .shorten-btn {
    width: 100%;
    height: fit-content;
    padding-block: 2vh;
    font-size: 1rem;
  }
}
</style>
