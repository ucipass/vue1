<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <a class="navbar-brand" href="/">Home</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdown"
              role="button"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
              >Menu</a
            >
            <div class="dropdown-menu" aria-labelledby="navbarDropdown">
              <router-link class="dropdown-item" to="/">Home</router-link>
              <router-link class="dropdown-item" to="/about">About</router-link>
              <div class="dropdown-divider"></div>
              <router-link class="dropdown-item" to="/awslogin"
                >Aws Login</router-link
              >
            </div>
          </li>
        </ul>
        <form class="form-inline my-2 my-lg-0">
          <input
            id="username"
            class="form-control mr-sm-2"
            type="search"
            placeholder="Username"
            aria-label="Username"
          />
          <input
            id="password"
            class="form-control mr-sm-2"
            type="password"
            placeholder="Password"
            aria-label="Pasword"
          />
          <button class="btn btn-outline-success my-2 my-sm-0" type="submit">
            Login
          </button>
        </form>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<style></style>
