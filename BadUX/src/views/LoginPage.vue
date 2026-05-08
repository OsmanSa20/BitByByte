<script setup>
import { ref } from 'vue'
import FakeInput from '../components/FakeInput.vue'

const email = ref('')
const password = ref('')

// Refs für die Ziel-Komponenten (die schwarzen Boxen)
const fakeEmailRef = ref(null)
const fakePasswordRef = ref(null)

// Funktionen zum Weiterleiten des Fokus
const focusEmail = () => {
  // .value.$el.focus() wird genutzt, falls FakeInput ein normales Input-Element ist
  // Falls FakeInput intern eine focus-Methode hat, nutzt man fakeEmailRef.value.focus()
  fakeEmailRef.value?.$el?.focus?.() || fakeEmailRef.value?.focus?.()
}

const focusPassword = () => {
  fakePasswordRef.value?.$el?.focus?.() || fakePasswordRef.value?.focus?.()
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
        <!-- @focus leitet den Klick sofort weiter -->
        <input 
          class="e-input" 
          type="text" 
          placeholder="Enter E-mail" 
          @focus="focusEmail"
        />
      </div>
      <div class="e-input-group">
        <p> Please Input Passwort </p>
        <input 
          class="e-input" 
          name='input' 
          type="password" 
          placeholder="Enter Password" 
          @focus="focusPassword"
        />
      </div>
    </div>

    <!-- Hier vergeben wir die ref-Attribute -->
    <FakeInput
      ref="fakeEmailRef"
      v-model="email"
      placeholder="E-Mail eingeben..."
      type="email"
    />
    
    <div style="width: 30px;"><p class="vertical">Die Länge ihres Namens</p> <p>___________</p> </div>
    
    <FakeInput
      ref="fakePasswordRef"
      v-model="password"
      placeholder="Passwort eingeben..."
      type="password"
    />
    <div class="vertical" style="width: 30px;"><p class="vertical">Die Länge ihres Passworts</p> <p>___________</p> </div>
  </div>
</template>

<style scoped>

@keyframes slideRightAndBack {
  0% {
    transform: translateX(-100%);
  }
  50% {
    transform: translateX(100vw);
  }
  100% {
    transform: translateX(-100%);
  }
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

#email-input , #password-input {
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

#vertical{
  writing-mode: vertical-rl;
  text-orientation: mixed;
  color: #333;
}

/* Optional: Die weißen Inputs leicht ausgrauen, 
   da sie nur noch als "Dummy" dienen */
.e-input {
  cursor: pointer;
}
</style>