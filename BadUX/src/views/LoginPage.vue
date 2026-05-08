<script setup>
import { ref } from 'vue'
import FakeInput from '../components/FakeInput.vue'

const email = ref('')
const password = ref('')

const fakeEmailRef = ref(null)
const fakePasswordRef = ref(null)

const focusEmail = () => {
  fakeEmailRef.value?.$el?.focus?.() || fakeEmailRef.value?.focus?.()
}

const errorSound = new Audio('/BadUX/src/assets/error.mp3')

function playErrorSound() {
  errorSound.currentTime = 0
  errorSound.play().catch(() => {})
}

const focusPassword = () => {
  fakePasswordRef.value?.$el?.focus?.() || fakePasswordRef.value?.focus?.()
}

function submitChaos() {
  const payload = {
    email: email.value,
    password: password.value
  }

  const encoded = btoa(JSON.stringify(payload))

  alert(
    "⚠️ SYSTEM OVERLOAD ⚠️\n\n" +
    "Base64 Payload:\n\n" +
    encoded
  )
}
</script>

<template>
  <div>
    <h1>Login</h1>

    <div id='input-container'>
      <div id="email-input">
        <p> Please Input Emeil </p>
        <input class="e-input-email" type="text" placeholder="Enter E-mail" v-model="email" />
      </div>

      <div id="password-input">
        <p> Please Imput Passwort </p>
        <input class="e-input-password" name='input' type="password" placeholder="Enter Password" v-model="password" />
        <span class="e-input-group-icon e-input-popup-date"></span>
      </div>

      <div id="email-input">
        <p> Please Input Email </p>
        <input class="e-input" type="text" placeholder="Enter E-mail" @focus="focusEmail" />
      </div>

      <div class="e-input-group">
        <p> Please Input Passwort </p>
        <input class="e-input" name='input' type="password" placeholder="Enter Password" @focus="focusPassword" />
      </div>
    </div>

    <FakeInput
      ref="fakeEmailRef"
      v-model="email"
      placeholder="E-Mail eingeben..."
      type="email"
    />

    <div style="width: 30px;">
      <p class="vertical">Die Länge ihres Namens</p>
      <p>___________</p>
    </div>

    <FakeInput
      ref="fakePasswordRef"
      v-model="password"
      placeholder="Passwort eingeben..."
      type="password"
    />

    <div class="vertical" style="width: 30px;">
      <p class="vertical">Die Länge ihres Passworts</p>
      <p>___________</p>
    </div>
  </div>

  <button
    class="chaos-submit"
    @click="submitChaos"
    @mouseenter="playErrorSound"
  >
    Submit
  </button>

  <div @click="() => errorSound.play().then(() => errorSound.pause())"></div>
</template>

<style scoped>
@keyframes slideRightAndBack {
  0% { transform: translateX(-100%); }
  50% { transform: translateX(100vw); }
  100% { transform: translateX(-100%); }
}

h1, p, #input-container {
  font-family: "Comic Sans MS", "Comic Sans", cursive;
}

h1 {
  font-size: 150px;
  color: #ff69b4;
  text-shadow: 2px 2px #ff1493;
  text-align: center;
  margin-left: -7%;
}

#email-input {
  animation: slideRightAndBack 30s linear infinite;
}

#email-input, #password-input {
  font-size: 150px;
  color: #333;
}

#password-input {
  animation: slideRightAndBack 30s linear infinite;
  animation-delay: 3s;
  font-size: 125px;
  color: #555;
}

.e-input-email {
  font-size: 25px;
  padding: 14px 18px;
  border: 5px solid #afa5a5;
  border-radius: 15px;
  width: 120%;
  background-color: #443a3a;
  color: #372828;
  margin-bottom: 20px;
}

.e-input-password {
  font-size: 25px;
  padding: 8px 12px;
  border: 5px solid #231919;
  border-radius: 6px;
  width: 10%;
  background-color: #ff8585;
}

#vertical {
  writing-mode: vertical-rl;
  text-orientation: mixed;
  color: #333;
}

.e-input {
  cursor: pointer;
}

.chaos-submit {
  font-size: 40px;
  font-family: "Comic Sans MS", cursive;

  padding: 20px 40px;

  background: linear-gradient(45deg, red, blue, lime, yellow);
  background-size: 400% 400%;

  border: 10px dotted magenta;
  border-radius: 50px;

  cursor: pointer;

  animation:
    rainbow 2s linear infinite,
    shake 0.5s infinite,
    spin 1s linear infinite;

  position: relative;
  left: 50%;
  transform: translateX(-50%);
}

@keyframes rainbow {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

@keyframes shake {
  0% { transform: translateX(-50%) translate(0px, 0px); }
  25% { transform: translateX(-50%) translate(3px, -3px); }
  50% { transform: translateX(-50%) translate(-3px, 3px); }
  75% { transform: translateX(-50%) translate(3px, 3px); }
  100% { transform: translateX(-50%) translate(0px, 0px); }
}

@keyframes spin {
  0% { filter: hue-rotate(0deg); }
  100% { filter: hue-rotate(360deg); }
}

.chaos-submit:hover {
  transform: scale(1.5) rotate(10deg);
  background: black;
  color: white;
}
</style>