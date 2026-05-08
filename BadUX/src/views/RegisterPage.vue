<template>
  <div class="register-page">
    <h1>Register</h1>

    <form class="register-form" @submit.prevent="onSubmit">
      <div>
        <p>Name</p>
        <input type="text" v-model="name" placeholder="Your name" required />
      </div>

      <div>
        <p>Email</p>
        <input type="email" v-model="email" placeholder="you@example.com" required />
      </div>

      <div>
        <p>Password</p>
        <input type="password" v-model="password" placeholder="Password" required />
      </div>

      <div>
        <p>Confirm Password</p>
        <input type="password" v-model="confirmPassword" placeholder="Confirm Password" required />
      </div>

      <div>
        <p>Security Question</p>
        <input type="text" v-model="securityQuestion" placeholder="Mother's maiden name?" />
      </div>

      <div>
        <button type="submit">Register</button>
      </div>
    </form>
  </div>
</template>

<script lang="ts">

</script>

<style scoped>
.register-page { padding: 12px; }
.register-form { width: 320px; }
.register-form p { margin: 6px 0 4px; font-size: 14px; }
.register-form input { padding: 6px; font-size: 14px; width: 100%; box-sizing: border-box; }
.register-form button { margin-top: 10px; padding: 8px 10px; }
</style>