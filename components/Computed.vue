<script>

export default {
  data() {
    return {
      shopNumber: 2,
      location: 'Bandung',
      city: 'Bandung',
      loginType: 'username',
      isShowing: false,
    }
  },
  computed: {
    count() {
      return this.shopNumber * 567;
    }
  },
  methods: {
    countMethod() {
      return 'The shop number is ' + this.shopNumber
    },
    toggleForm() {
      if (this.loginType === 'username') {
        this.loginType = 'email';
      } else {
        this.loginType = 'username';
      }
    }
  }
}
</script>

<template>
  <div>
    <h1>{{ count }}</h1>
    <div v-show="loginType === 'username'">
      <label>Username</label>
      <input placeholder="Enter your username" key="username-input">
    </div>
    <div v-show="loginType === 'email'">
      <label>Email</label>
      <input placeholder="Enter your email address" key="email-input">
    </div>
    <button type="button" @click="toggleForm">Toggle Form</button>
    <div>
      <p v-show="isShowing">Mencoba show</p>
      <button type="button" @click="isShowing = !isShowing">Toggle Show</button>
    </div>
  </div>
</template>

<style scoped>

</style>
