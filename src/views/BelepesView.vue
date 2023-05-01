<template>
  <div>
      <h3 class="text-center mt-5 mb-5">Belépés munkatársaink részére:</h3>
    </div>
    
    <div class="login-page">
  <div class="form" >
    <form class="login-form"  method="post">
      <input type="text" placeholder="Felhasználónév" v-model="username"/>
      <input type="password" placeholder="Jelszó" v-model="password"  @keyup.enter="login()" />
      <input value="Belépés" type="button" class="btn" id="submit" @click="login()" />
    </form>
  </div>
</div>
</template>

<script>
import { loginUser } from '@/store/auth.js';

//https://chrismroberts.com/2019/01/03/authentication-and-protected-routes-in-vuejs/
export default {
    data() {
        return {
            username: '',
            pw: ''
        }
    },
    methods: {
        async login() {
          try {

            await loginUser(this.username, "admin")
                this.$router.push('/boltok')
            }
            catch (err) {
                alert(`Error: ${err}`)
            }
        }
    }
}


</script>



<style>
@import url(https://fonts.googleapis.com/css?family=Roboto:300);

.login-page {
  width: 360px;
  padding: 8% 0 0;
  margin: auto;
}
.form {
  position: relative;
  z-index: 1;
  background: transparent;
  max-width: 360px;
  margin: 0 auto 100px;
  padding: 45px;
  text-align: center;
  box-shadow: 0 6px 20px 14px rgba(0, 0, 0, 0.2), 0 5px 5px 0 rgba(0, 0, 0, 0.24);
}
.form input {
  font-family: "Roboto", sans-serif;
  outline: 0;
  background: rgba(242, 242, 242);
  width: 100%;
  border: 0;
  margin: 0 0 15px;
  padding: 15px;
  box-sizing: border-box;
  font-size: 14px;
}
.form #submit {
  font-family: "Roboto", sans-serif;
  text-transform: uppercase;
  outline: 0;
  background: #4CAF50;
  width: 100%;
  border: 0;
  padding: 15px;
  text-align:center;
  color: #FFFFFF;
  font-size: 14px;
  -webkit-transition: all 0.3 ease;
  transition: all 0.3 ease;
  cursor: pointer;
}
.form #submit:hover,.form #submit:active,.form #submit:focus {
  background: #43A047;
}
.form .message {
  margin: 15px 0 0;
  color: #b3b3b3;
  font-size: 12px;
}
.form .message a {
  color: #4CAF50;
  text-decoration: none;
}
.form .register-form {
  display: none;
}
.container {
  position: relative;
  z-index: 1;
  margin: 0 auto;
}
.container:before, .container:after {
  content: "";
  display: block;
  clear: both;
}

.container .info span {
  color: #4d4d4d;
  font-size: 12px;
}
.container .info span a {
  color: #000000;
  text-decoration: none;
}
.container .info span .fa {
  color: #EF3B3A;
}
body {
  font-family: "Roboto", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;      
}

.loginIcon {
  height: 25px;
  display: none;
}

</style>