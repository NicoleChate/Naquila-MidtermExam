<template>
  <div>
    <nav class="navbar navbar expand navbar-dark bg-dark px-3">
      <router-link class="navbar-brand" to="/">Student Registration Form</router-link>
      <div class="navbar-nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/registration">Registration</router-link>
      </div>
    </nav>
    <hr />
    <router-view />
  </div>
</template>
