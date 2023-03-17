<template>
    <div>
      <h1>Register</h1>
      <form>
        <div>
          <label for="username">Username</label>
          <input type="text" id="username" v-model="username">
        </div>
        <div>
          <label for="email">Email</label>
          <input type="email" id="email" v-model="email">
        </div>
        <div>
          <label for="password">Password</label>
          <input type="password" id="password" v-model="password">
        </div>
        <div>
          <label for="confirm-password">Confirm Password</label>
          <input type="password" id="confirm-password" v-model="confirmPassword">
        </div>
        <button type="submit">Register</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        email: '',
        password: '',
        confirmPassword: ''
      }
    }}
  </script>
  
  <style lang="scss" scoped>
  h1 {
    font-size: 2.5rem;
    margin-bottom: 2rem;
    text-align: center;
  }
  form {
    max-width: 500px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    
    label {
    font-size: 1.5rem;
    margin-top: 2rem;
  }
  }
  input {
    font-size: 1.5rem;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    border: 2px solid #ccc;
    margin-top: 1rem;
  }
  button {
    margin-top: 2rem;
    font-size: 1.5rem;
    padding: 1rem;
    border-radius: 0.5rem;
    background-color: #2aceeb;
    color: #030e1b;
    border: none;
    cursor: pointer;
  }
  </style>
  