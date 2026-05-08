<template>
  <div>
    <h1>Login</h1>


    <div id='input-container'>
            <div id="email-input">
                <p> Please Input Emeil </p>
                <input class="e-input" type="text" placeholder="Enter E-mail" />
            </div>
            <div class="e-input-group">
                <p> Please Input Passwort </p>
                <input class="e-input" name='input' type="password" placeholder="Enter Password" />
                <span class="e-input-group-icon e-input-popup-date"></span>
            </div>
    </div>

  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'LoginPage',
});
</script>

<style scoped>

h1, #input-container {
  font-family: Comic Sans MS;
} 

#email-input {
  margin-left: 80px;
}

#email-input p {
  font-size: 20px;
  color: #333;
}



</style>