<template>
  <div id="app">
    <header class="navbar navbar-light bg-dark">
      <router-link class="navbar-brand" to="/"><img src="./assets/logo.svg"></router-link>
    </header>
    <div class="jumbotron jumbotron-fluid">
      <div class="container">
        <h1 class="display-4">Some photos maybe?</h1>
        <hr>
        <p class="lead">yes please br0</p>
      </div>
    </div>
    <div class="navbar-nav navbar-light bg-light">
      <div class="container">
        <ul class="nav nav-pills nav-fill">
          <li class="nav-item">
            <router-link to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/about">About</router-link>
          </li>
          <li class="nav-item">Bla bla</li>
        </ul>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-3 side-panel">
          <p>side panel</p>
        </div>
        <div class="col-9 content">
          <router-view/>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.jumbotron {
  margin-bottom: 0;
}
.navbar-nav {
  margin-bottom: 30px;
}
.content {
  border: solid 1px #aaa;
  background-color: #eee;
}
.side-panel {
  border: solid 1px #aaa;
  background-color: #ddd;
}
</style>
