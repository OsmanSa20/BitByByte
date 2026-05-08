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
h1, p, #input-container {
  font-family: "Comic Sans MS", "Comic Sans", cursive;
} 

#email-input {
  margin-left: 80px;
}

#email-input p {
  font-size: 20px;
  color: #333;
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