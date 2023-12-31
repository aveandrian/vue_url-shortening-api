<script setup lang="ts">
import LinkShortener from './components/LinkShortener.vue'
import Navbar from './components/Navbar.vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import {
  faFacebookSquare,
  faTwitter,
  faPinterest,
  faInstagram
} from '@fortawesome/free-brands-svg-icons'
</script>

<template>
  <Navbar />
  <section className="header-section">
    <div className="header-description">
      <h1 className="header-title">More than just shorter links</h1>
      <p className="header-text">
        Build your brand's recognition and get detailed insights on how your
        links are performing.
      </p>
      <button className="get-started-btn ">Get Started</button>
    </div>
    <img
      className="header-img"
      src="/images/illustration-working.svg"
      alt="Header Illustration"
    />
  </section>
  <section class="stats">
    <LinkShortener />
    <h1 class="stats-title">Advanced Statistics</h1>
    <p class="stats-text">
      Track how your links are performing across the web with our advanced
      statistics dashboard.
    </p>
    <div class="stats-items-wrapper">
      <div class="connector"></div>
      <div class="stats-item stats-1">
        <div class="stats-img-wrapper">
          <img
            class="stats-item-img"
            src="/images/icon-brand-recognition.svg"
            alt="Icon Brand Recognition"
          />
        </div>
        <h2 class="stats-item-title">Brand Recognition</h2>
        <p class="stats-item-text">
          Boost your brand recognition with each click. Generic links don’t mean
          a thing. Branded links help instil confidence in your content.
        </p>
      </div>
      <div class="stats-item stats-2">
        <div class="stats-img-wrapper">
          <img
            class="stats-item-img"
            src="/images/icon-detailed-records.svg"
            alt="Icon Detailed Records"
          />
        </div>
        <h2 class="stats-item-title">Detailed Records</h2>
        <p class="stats-item-text">
          Gain insights into who is clicking your links. Knowing when and where
          people engage with your content helps inform better decisions.
        </p>
      </div>
      <div class="stats-item stats-3">
        <div class="stats-img-wrapper">
          <img
            class="stats-item-img"
            src="/images/icon-fully-customizable.svg"
            alt="Icon Fully Customizable"
          />
        </div>
        <h2 class="stats-item-title">Fully Customizable</h2>
        <p class="stats-item-text">
          Improve brand awareness and content discoverability through
          customizable links, supercharging audience engagement.
        </p>
      </div>
    </div>
  </section>
  <section class="boost-section">
    <h1 class="boost-title">Boost your links today</h1>
    <button class="get-started-btn">Get Started</button>
  </section>
  <section class="footer-section">
    <div class="footer-content">
      <img class="footer-logo" src="/images/logo.svg" alt="Logo" />
      <div class="links-section">
        <h2 class="links-section-title">Features</h2>
        <a>Link Shortening</a>
        <a>Branded Links</a>
        <a>Analytics</a>
      </div>
      <div class="links-section">
        <h2 class="links-section-title">Resources</h2>
        <a>Blog</a>
        <a>Developers</a>
        <a>Support</a>
      </div>
      <div class="links-section">
        <h2 class="links-section-title">Company</h2>
        <a>About</a>
        <a>Our Team</a>
        <a>Careers</a>
        <a>Contact</a>
      </div>
      <div class="socials">
        <FontAwesomeIcon
          :icon="faFacebookSquare"
          size="xl"
          class="social-icon"
        />
        <FontAwesomeIcon :icon="faTwitter" size="xl" class="social-icon" />
        <FontAwesomeIcon :icon="faPinterest" size="xl" class="social-icon" />
        <FontAwesomeIcon :icon="faInstagram" size="xl" class="social-icon" />
      </div>
    </div>
    <div class="attribution">
      Challenge by
      <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
        >Frontend Mentor</a
      >. Coded by <a href="https://github.com/aveandrian">aveandrian</a>.
    </div>
  </section>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

body {
  min-height: 100vh;
}

#app {
  position: relative;
  overflow: hidden;
}

.header-section {
  overflow: hidden;
  margin-block: 5vh;
  margin-bottom: 12vh;
  display: flex;
  align-items: center;
  padding-left: 10vw;
}

.header-description {
  display: flex;
  flex-direction: column;
  align-items: start;
}

.header-title {
  font-size: 4.5rem;
  line-height: 1.1em;
  font-weight: 700;
  color: hsl(255, 11%, 22%);
}

.header-text {
  width: 60%;
  margin-bottom: 3vh;
  line-height: 1.5em;
  color: hsl(257, 7%, 63%);
}

.get-started-btn {
  border: none;
  border-radius: 1.25rem;
  color: white;
  background-color: hsl(180, 66%, 49%);
  padding: 0.625rem 1.875rem;
}

.get-started-btn:hover {
  cursor: pointer;
  background-color: #9be3df;
}

.header-img {
  width: 50%;
  transform: translateX(10%);
}

.stats {
  padding-inline: 10vw;
  padding-bottom: 15vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #f0f1f6;
}

.stats-items-wrapper {
  position: relative;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  column-gap: 2vw;
  margin-block: 6vh;
}

.connector {
  position: absolute;
  width: 100%;
  top: 50%;
  height: 1vh;
  background-color: #2ad0ce;
}

.stats-item {
  z-index: 1;
  background-color: white;
  border-radius: 0.625rem;
  padding: 1.25rem;
  padding-top: 3.125rem;
  position: relative;
}

.stats-img-wrapper {
  position: absolute;
  top: 0;
  width: 5rem;
  height: 5rem;
  border-radius: 50%;
  background-color: #3a3053;
  display: flex;
  align-items: center;
  justify-content: center;
  transform: translateY(-50%);
}

.stats-2 {
  transform: translateY(15%);
}

.stats-3 {
  transform: translateY(30%);
}

.boost-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 2vh;
  padding-block: 5vh;
  background: url('/images/bg-boost-desktop.svg'), #3a3053;
}

.boost-title {
  color: white;
  font-size: 2rem;
}

.footer-section {
  display: flex;
  flex-direction: column;
  padding-inline: 10vw;
  padding-block: 5vh;
  background: #232027;
}

.footer-content {
  display: flex;
  align-items: start;
  gap: 4vw;
  color: white;
}

.footer-logo {
  margin-right: 15vw;
  filter: brightness(0) invert(1);
}

.links-section {
  display: flex;
  flex-direction: column;
  gap: 1vh;
}

.links-section-title {
  font-size: 1rem;
  margin-bottom: 2vh;
}

.links-section a {
  color: hsl(0, 0%, 75%);
}

.links-section a:hover {
  cursor: pointer;
  color: hsl(180, 66%, 49%);
}

.socials {
  margin-left: auto;
  display: flex;
  gap: 1vw;
}

.social-icon {
  color: white;
}

.social-icon:hover {
  cursor: pointer;
  color: hsl(180, 66%, 49%);
}

.attribution,
.attribution a {
  margin-top: 4vh;
  text-align: center;
  color: hsl(0, 0%, 75%);
}

.attribution a:hover {
  cursor: pointer;
  color: hsl(180, 66%, 49%);
}

@media screen and (max-width: 60rem) {
  .header-section {
    display: grid;
    grid-template-columns: 1fr;
    padding-left: 5vw;
    margin: 0;
  }

  .header-img {
    grid-row: 1;
    width: 100%;
  }

  .header-description {
    padding-right: 5vw;
    text-align: center;
    align-items: center;
    grid-row: 2;
  }

  .header-title {
    font-size: 2.5rem;
  }

  .header-text {
    width: 95%;
  }

  .stats {
    padding-inline: 5vw;
    align-items: center;
    text-align: center;
  }

  .stats-items-wrapper {
    display: flex;
    flex-direction: column;
    gap: 10vh;
    margin-block: 10vh;
  }

  .stats-img-wrapper {
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .connector {
    position: absolute;
    width: 2vw;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    height: 100%;
  }

  .boost-section {
    padding-inline: 5vw;
    padding-block: 12vh;
    text-align: center;
    background: url('/images/bg-boost-mobile.svg'), #3a3053;
    background-size: 100% 100%;
  }

  .boost-title {
    font-size: 1.8rem;
  }

  .footer-content {
    flex-direction: column;
    align-items: center;
    text-emphasis: center;
    gap: 5vh;
  }

  .footer-logo {
    margin: 0;
  }

  .links-section {
    align-items: center;
    text-align: center;
  }

  .socials {
    margin: 0;
    gap: 2vw;
  }
}
</style>
