<script setup>
import { ref } from 'vue'

const logi = ref({
  username: '',
  password: '',
})

const usuario = ref({
  nombre: '',
  apellido: '',
  sexo: '',
  edad: '', 
  conocimientos: [],
  admin: false,
  observaciones: '',
  grupo: '',
})

let cambio = ref(true)
let cambioForm = ref(true)

function validateLogin() {
  const username = document.getElementById("username").value;
  const password = document.getElementById("password").value;

  // Verificar si los campos están llenos
  if (username.trim() === '' || password.trim() === '') {
  alert("Por favor, ingresa el nombre de usuario y la contraseña.");
  return;
  }

  // Verificar si los datos coinciden con los del objeto users
  if (logi.hasOwnProperty(username) && logi.hasOwnProperty(password) === password) {
  alert("Inicio de sesión exitoso.");
  document.getElementById("login").submit();
  } else {
  alert("Nombre de usuario o contraseña incorrectos.");
  }
}

function forms(event){
  cambioForm.value = false
}

function mostrarDatos(event) {
  // event.preventDefault()
  console.log(usuario.value);
  cambio.value = false
}

</script>

<template>

  <form v-if="cambio" id="registro"> 
      
    <legend>Registro</legend>
    <label for="nombre">Nombre
      <input type="text" id="nombre" v-model="usuario.nombre">
    </label>
    <br>
    <label for="apellido">
      Apellido
      <input type="text" id="apellido" v-model="usuario.apellido">
    </label>
    <br>
    <label>
      Sexo
      <br>
      <label for="sexo-M">
        Masculino
        <input type="radio" id="sexo-M" name="sexo" value="M" v-model="usuario.sexo">
      </label>
      <label for="sexo-F">
        Femenino
        <input type="radio" id="sexo-F" name="sexo" value="F" v-model="usuario.sexo">
      </label>
    </label>
    <br>
    <label for="edad">
      Edad
      <input type="number" id="edad" max="100" min="16" v-model="usuario.edad">
    </label>
    <br>
    <label for="user">
      Correo
      <input type="email" id="user" v-model="logi.username" required>
    </label>
    <br>
    <label for="password">
      Contraseña
      <input type="password" id="password" v-model="logi.password">
    </label>
    <br>
    <label for="conocimientos">
      Conocimientos
      <br>
      <label for="HTML">
        <input type="checkbox" id="HTML" value="HTML" v-model="usuario.conocimientos"> HTML
      </label>
      <label for="CSS">
        <input type="checkbox" id="CSS" value="CSS" v-model="usuario.conocimientos"> CSS
      </label>
      <label for="JS">
        <input type="checkbox" id="JS" value="JS" v-model="usuario.conocimientos"> JavaScript
      </label>
      <label for="Vue">
        <input type="checkbox" id="Vue" value="Vue" v-model="usuario.conocimientos"> Vue.js
      </label>
    </label>
    <br>
    <label for="permisos">
      <input type="checkbox" id="permisos" v-model="usuario.admin">
      ¿Usuario administrador?
    </label>
    <br>
    <label for="observaciones">
      Observaciones
      <br>
      <textarea id="observaciones" cols="30" rows="10" v-model="usuario.observaciones"></textarea>
    </label>
    <br>
    <label for="menu">
      Grupo
      <select id="menu" v-model="usuario.grupo">
        <option value="" selected>...</option>
        <optgroup label="seccion 1">
          <option value="1-1">Uno</option>
          <option value="1-2">Dos</option>
          <option value="1-3">Tres</option>
        </optgroup>
        <optgroup label="seccion 2">
          <option value="2-1">Uno</option>
          <option value="2-2">Dos</option>
          <option value="2-3">Tres</option>
        </optgroup>
      </select>
    </label>

    <br>
    <button @click="mostrarDatos">Guardar</button>
    <input type="reset" name="Borrar">
    <button @click="forms">
    <a href="">Ya tengo una cuenta</a>
    </button>
  </form>


  <div v-else id="login">
    <form id="loginForm">
        <label for="username">Usuario:</label>
        <input type="text" id="username" name="username" required>
        <br>
        <label for="password">Contraseña:</label>
        <input type="password" id="password" name="password" required>
        <br>
    <button @click="validateLogin()">ingresar</button>
    <a href="#registro">Registrarme</a>
  </form>
  </div>

  

</template>
