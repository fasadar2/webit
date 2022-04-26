<template>
<div class="form-div">
<img class="logo_big" src="../assets/logo.png">
<form class="form">
<img class="logo" src="../assets/logo.png">
<h3 class="form_title">Вход</h3>
<p>
<input type="text" id="log" class="form_input" placeholder="Логин">
</p>
<p class="checkbox" >
<input type="password" id="password" class="form_input" placeholder="Пароль">
</p>
<p>
<button type="button" v-on:click="signIn" class="form_btn">Войти</button>
</p>
</form>
</div>
</template>
<script lang="ts">
import Vue from 'vue';
import axios from 'axios';

export default Vue.extend({
  name: 'Enter',
  props: {
  },
  methods: {
    toggleStyleEnter() {
      const enter :HTMLDivElement = document.querySelector('.autorization_block');
      const reg :HTMLDivElement = document.querySelector('.registrationtion_block');
      const enterBtn :HTMLDivElement = document.querySelector('.EnterBtn');
      const regBtn :HTMLDivElement = document.querySelector('.RegBtn');
      enter.style.display = 'flex';
      reg.style.display = 'none';
      enterBtn.style.color = 'green';
      regBtn.style.color = 'black';
    },
    toggleStyleRegister() {
      const enter :HTMLDivElement = document.querySelector('.autorization_block');
      const reg :HTMLDivElement = document.querySelector('.registrationtion_block');
      const enterBtn :HTMLDivElement = document.querySelector('.EnterBtn');
      const regBtn :HTMLDivElement = document.querySelector('.RegBtn');
      enter.style.display = 'none';
      reg.style.display = 'flex';
      enterBtn.style.color = 'black';
      regBtn.style.color = 'green';
    },
    signIn() {
      const log :HTMLInputElement = document.getElementById('log') as HTMLInputElement;
      const password :HTMLInputElement = document.getElementById('password') as HTMLInputElement;
      const config = {
        url: 'https://a02f853a-6182-4e81-ac3e-eba5acd42df0.mock.pstmn.io/auth/sign',
      };
      const data = {
        login: log.value,
        password: password.value,
      };
      axios.post(config.url, data, { headers: { 'x-mock-match-request-body': true } })
        .then((response) => {
          console.log(response.data.isValid);
          if (response.data.isValid) {
            alert('Успешно!');
          }
        })
        .catch((error) => {
          console.log(error);
          alert('Неверный логин или пароль!');
        });
    },
    signOn() {
      const regLog :HTMLInputElement = document.getElementById('regLog') as HTMLInputElement;
      const regPass :HTMLInputElement = document.getElementById('regPass') as HTMLInputElement;
      const regPass2 :HTMLInputElement = document.getElementById('regPass2') as HTMLInputElement;
      const regEmail :HTMLInputElement = document.getElementById('regEmail') as HTMLInputElement;
      const config = {
        url: 'https://a02f853a-6182-4e81-ac3e-eba5acd42df0.mock.pstmn.io/auth/check',
      };
      const data = {
        login: regLog.value,
      };
      if (regEmail.value === '') {
        alert('Введите почту!');
        return;
      }
      if (regLog.value === '') {
        alert('Введите логин!');
        return;
      }
      if (regPass.value === '') {
        alert('Введите пароль!');
        return;
      }
      if (regPass.value !== regPass2.value) {
        alert('Пароли не совпадают!');
        return;
      }
      axios.post(config.url, data, { headers: { 'x-mock-match-request-body': true } })
        .then((response) => {
          console.log(response.data.isValid);
          if (response.data.isValid) {
            alert('Логин занят!');
          }
        })
        .catch((error) => {
          console.log(error);
          alert('Успешно!');
        });
    },
  },
});
</script>
<style scoped>
.form-div {
width: 80%;
height: 600px;
display: flex;
justify-content: space-between;
}
.logo_big {
width: 40%;
height:60%;
background: #444;
}
.logo {
display: none;
width: 30px;
padding-top: 10px;
}
.form {
width: 50%;
margin-left: 40px;
}
.form_title {
font-size: 1.5rem;
font-weight: 500;
color: #333;
}
.form_input {
width: 80%;
padding: 10px;
border: solid 1px #333;
font-size: inherit;
}
.checkbox {
}
.form_btn {
border: none;
cursor: pointer;
font-size: inherit;
background-color: #03a9f4;
color: #fff;
padding: 10px 50px;
}
@media(max-width: 768px) {
.form-div {
height: 300px;
}
.logo_big {
display: none;
}
.logo {
display: flex;
}
}
@media(max-width: 480px) {
.form-div {
width: 300px;
}
}
</style>
