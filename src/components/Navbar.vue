<template>
  <div>
    <div id="navbar-main">
      <nav
        class="navbar navbar-expand-lg navbar-dark bg-dark static-top"
        role="navigation"
      >
        <a class="navbar-brand" href="/" style="font-size:1em; color:white">
          <i class="fas fa-home"></i>
        </a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarNavDropdown"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavDropdown">
          <ul class="navbar-nav">
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdownMenuLink"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
                >Menu</a
              >
              <div
                class="dropdown-menu"
                aria-labelledby="navbarDropdownMenuLink"
              >
                <a class="dropdown-item" href="test">Test</a>
                <a class="dropdown-item" href="files">Files</a>
                <a class="dropdown-item" href="charts">Charts</a>
                <a class="dropdown-item" href="users">Users</a>
                <a class="dropdown-item" href="settings">Settings</a>
              </div>
            </li>
          </ul>
          <form id="loginForm" class="ml-auto form-inline my-2 my-lg-0">
            <input
              id="user"
              class="form-control mr-sm-2 d-none"
              type="text"
              placeholder="username"
              aria-label="username"
            />
            <input
              id="pass"
              class="form-control mr-sm-2 d-none"
              type="password"
              placeholder="password"
              aria-label="password"
              autocomplete="current password"
            />
            <button
              id="login"
              class="btn btn-outline-success my-2 my-sm-0 d-none"
              type="submit"
            >
              Login
            </button>
            <button
              id="logout"
              class="btn btn-outline-success my-2 my-sm-0 d-none"
              type="submit"
            >
              Logout
            </button>
          </form>
        </div>
      </nav>
    </div>
    <div class="modal fade" id="modalAlert" role="dialog">
      <div class="modal-dialog modal-sm">
        <div class="modal-content">
          <div class="modal-body alert-danger">
            <p id="modalAlertText">Alert!</p>
            <button
              type="button"
              class="btn btn-secondary ml-auto"
              data-dismiss="modal"
            >
              Close
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
