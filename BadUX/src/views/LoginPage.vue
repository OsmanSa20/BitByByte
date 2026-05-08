<template>
  <div>
    <h1>Login</h1>


    <div id='input-container'>
            <div id="email-input">
                <p> Please Input Emeil </p>
                <input class="e-input-email" type="text" placeholder="Enter E-mail" />
            </div>
            <div id="password-input">
                <p> Please Imput Passwort </p>
                <input class="e-input-password" name='input' type="password" placeholder="Enter Password" />
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



</style>