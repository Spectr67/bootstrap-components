<script>
import { BTabs, BTab, BButton, BFormInput, BForm } from 'bootstrap-vue-next'

export default {
  components: { BTabs, BTab, BButton, BFormInput, BForm },

  data() {
    return {
      isLoggedIn: false,
      userEmail: '',
      regEmail: '',
      regPassword: '',
      loginEmail: '',
      loginPassword: '',
      q: 0,
    }
  },
  methods: {
    register() {
      if (this.regEmail && this.regPassword) {
        this.userEmail = this.regEmail
        this.isLoggedIn = true
      }
    },
    login() {
      if (this.loginEmail && this.loginPassword) {
        this.userEmail = this.loginEmail
        this.isLoggedIn = true
      }
    },
    logout() {
      this.isLoggedIn = false
      this.regEmail = ''
      this.regPassword = ''
      this.loginEmail = ''
      this.loginPassword = ''
    },
  },
}
</script>

<template>
  <b-tabs v-if="!isLoggedIn" v-model="q">
    <b-tab title="Главная" :active="q == 0">
      <div class="p-3">
        <h3>Добро пожаловать!</h3>
        <p>Выберите действие:</p>
        <b-button variant="primary" @click="q = 1">Регистрация</b-button>
        <b-button variant="success" class="ms-2" @click="q = 2">Логин</b-button>
      </div>
    </b-tab>

    <b-tab title="Регистрация" :active="q == 1">
      <div class="p-3">
        <h4>Регистрация</h4>
        <b-form>
          <b-form-input v-model="regEmail" placeholder="Email"></b-form-input>
          <b-form-input
            v-model="regPassword"
            placeholder="Пароль"
            type="text"
            class="mt-2"
          ></b-form-input>
        </b-form>
        <b-button variant="primary" class="mt-3" @click="register">
          Зарегистрироваться
        </b-button>
      </div>
    </b-tab>

    <b-tab title="Логин" :active="q == 2">
      <div class="p-3">
        <h4>Вход</h4>
        <b-form>
          <b-form-input v-model="loginEmail" placeholder="Email"></b-form-input>
          <b-form-input
            v-model="loginPassword"
            placeholder="Пароль"
            type="text"
            class="mt-2"
          ></b-form-input>
        </b-form>
        <b-button variant="success" class="mt-3" @click="login">Войти</b-button>
      </div>
    </b-tab>
  </b-tabs>

  <div v-else class="p-3">
    <h3>Здравствуйте, {{ userEmail }}!</h3>
    <b-button variant="danger" @click="logout">Выйти</b-button>
  </div>
</template>
