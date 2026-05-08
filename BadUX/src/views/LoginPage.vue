<template>
  <div>
    <h1>Login</h1>


    <div id='input-container'>
            <p> Please Input E-mail </p>
            <input class="e-input" type="text" placeholder="Enter E-mail" />
            <div class="e-input-group">
                <p> Please Input Passwort </p>
                <input class="e-input" name='input' type="password" placeholder="Enter Passwort" />
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
h1,p, .input-container {
  font-family: "Comic Sans MS", "Comic Sans", cursive;
} 

</style>