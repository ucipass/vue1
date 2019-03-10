<template>
  <div class="container">
    <h1 class="text-center">AWS Cognito Login Test</h1>
    <br />
    <div class="row">
      <div class="col-6">
        <div class="aws">
          <form>
            <div class="form-group">
              <label for="UserPoolId">AWS Cognito UserPoolId</label>
              <input
                id="UserPoolId"
                class="form-control"
                type="text"
                placeholder="UserPoolId"
                aria-label="UserPoolId"
                value="us-east-2_EOoVfjL76"
              />
            </div>
            <div class="form-group">
              <label for="ClientId">AWS Cognito ClientId</label>
              <input
                id="ClientId"
                class="form-control"
                type="text"
                placeholder="ClientId"
                aria-label="ClientId"
                value="68udbgdarsu9t6jje8h9i15kfu"
              />
            </div>
            <div class="form-group">
              <label for="ClientId">AWS Cognito Username</label>
              <input
                id="awsusername"
                class="form-control"
                type="text"
                placeholder="Username"
                aria-label="Username"
              />
            </div>
            <div class="form-group">
              <label for="ClientId">AWS Cognito Password</label>
              <input
                id="awspassword"
                class="form-control mr-sm-2"
                type="password"
                placeholder="Password"
                aria-label="Pasword"
              />
            </div>
            <div class="form-group">
              <button
                v-on:click="awslogin"
                class="btn btn-outline-success my-2 my-sm-0"
                type="submit"
              >
                Login
              </button>
            </div>
          </form>
        </div>
      </div>
      <div class="col-6">
        <form>
          <div class="form-group">
            <label for="awsoutput">AWS Output</label>
            <textarea class="form-control" rows="4" id="awsoutput"></textarea>
          </div>
          <div class="form-group">
            <label for="idToken">AWS idToken</label>
            <textarea class="form-control" rows="7" id="idToken"></textarea>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import {
  CognitoUserPool,
  AuthenticationDetails,
  CognitoUser
} from "amazon-cognito-identity-js";
import { setCookie, getCookie } from "@/components/cookie.js";

let idToken = getCookie("idToken");
let awsusername = getCookie("username");
let UserPoolId = getCookie("UserPoolId");
let ClientId = getCookie("ClientId");

// eslint-disable-next-line no-console
console.log("Cookie", awsusername, idToken);

function awslogin() {
  awsusername = document.getElementById("awsusername").value;
  UserPoolId = document.getElementById("UserPoolId").value;
  ClientId = document.getElementById("ClientId").value;
  setCookie("awsusername", awsusername, 1);
  setCookie("UserPoolId", UserPoolId, 1);
  setCookie("ClientId", ClientId, 1);
  let awspassword = document.getElementById("awspassword").value;
  var poolData = {
    UserPoolId: UserPoolId, // Your user pool id here
    ClientId: ClientId // Your client id here
  };
  var userPool = new CognitoUserPool(poolData);
  var authenticationDetails = new AuthenticationDetails({
    Username: awsusername,
    Password: awspassword
  });
  let userData = {
    Username: awsusername,
    Pool: userPool
  };
  let cognitoUser = new CognitoUser(userData);
  cognitoUser.authenticateUser(authenticationDetails, {
    onSuccess: result => {
      //document.getElementById("p1").innerHTML = "You are logged in";
      // eslint-disable-next-line no-unused-vars
      let hold = result;
      //console.log(cognitoUser);
      let idToken = cognitoUser.signInUserSession.idToken.jwtToken;
      setCookie("idToken", idToken, 1);
      document.getElementById("awsoutput").innerHTML = idToken;
      // eslint-disable-next-line no-console
      console.log("Cognito Token:\n" + idToken);
    },
    onFailure: err => {
      setCookie("idToken", "", 1);
      document.getElementById("idToken").innerHTML = "";
      document.getElementById("awsoutput").innerHTML = err.message;
      // eslint-disable-next-line no-console
      console.log(err.message);
    }
  });
}

export default {
  name: "aws",
  methods: {
    awslogin: awslogin
  },
  mounted() {
    document.getElementById("awsusername").value = getCookie("awsusername");
    document.getElementById("UserPoolId").value = getCookie("UserPoolId");
    document.getElementById("ClientId").value = getCookie("ClientId");
    document.getElementById("idToken").value = getCookie("idToken");
    // eslint-disable-next-line no-console
    console.log("MOUNT TEMPLATES");
  }
};
</script>

<style scoped>
.mystyle {
  margin-top: 10px;
  margin-bottom: 10px;
  margin-right: 10px;
  margin-left: 10px;
  width: 300px;
}
</style>
