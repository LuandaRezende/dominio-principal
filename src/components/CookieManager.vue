<template>
    <div>
      <h2>Gerenciar Cookie</h2>
      <div>
        <label for="cookieName">Nome:</label>
        <input type="text" id="cookieName" v-model="cookieName">
      </div>
      <div>
        <label for="cookieValue">Valor:</label>
        <input type="text" id="cookieValue" v-model="cookieValue">
      </div>
      <div>
        <button @click="setCookie">Definir Cookie</button>
      </div>
      <div>
        <h3>Cookies Atuais:</h3>
        <pre>{{ cookies }}</pre>
      </div>
      <button @click="readCookies">Ler Cookies</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        cookieName: '',
        cookieValue: '',
        cookieDomain: '.localhost',
        cookies: ''
      };
    },
    methods: {
      setCookie() {
        document.cookie = `${this.cookieName}=${this.cookieValue}; domain=${this.cookieDomain}; path=/`;
        this.cookieName = '';
        this.cookieValue = '';
      },
      readCookies() {
        this.cookies = document.cookie;
      }
    },
    mounted() {
      this.readCookies();
    }
  };
  </script>
  
  <style scoped>
  /* Estilos opcionais para este componente */
  label {
    display: inline-block;
    width: 80px;
    margin-bottom: 5px;
  }
  input[type="text"] {
    width: 200px;
    padding: 5px;
    margin-bottom: 10px;
  }
  button {
    padding: 8px 15px;
    cursor: pointer;
  }
  pre {
    margin-top: 10px;
    border: 1px solid #ccc;
    padding: 10px;
    background-color: #f4f4f4;
  }
  </style>