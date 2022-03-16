<template>
<div class="form-div">
<img class="logo_big" src="../assets/logo.png">
<form class="form">
<img class="logo" src="../assets/logo.png">
<h3 class="form_title">Вход</h3>
<p>
<input type="text" class="form_input" placeholder="Логин">
</p>
<p class="checkbox" >
<input type="password" class="form_input" placeholder="Пароль">
</p>
<p>
<input type="checkbox">
<span>Запомнить данные пользователя</span>
</p>
<p>
<button class="form_btn">Войти</button>
</p>
</form>
</div>
</template>
<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'Login',
  props: {
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
