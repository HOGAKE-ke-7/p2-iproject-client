<template>
  <section>
    <!-- <h1>masuk login</h1> -->
    <br> <br> <br>
    <div class="container">
    <div class="row">
        <div class="col-md-6 offset-sm-1">
            <div class="card">
                <form @submit.prevent="login" class="box">
                    <h1>Login</h1>
                    <p class="text-muted"> Please enter your login and password!</p>
                    <input type="text" v-model="user.email" name="email" placeholder="input your email">
                    <input type="password" v-model="user.password" name="password" placeholder="input your password">
                    <a @click="toRegister" class="forgot text-muted pointer" >Don't have an account? Register here</a>
                    <input type="submit" value="Login">
                <div class="col-sm-12 d-flex justify-content-center">
                  <button v-google-signin-button="clientId" class="google-signin-button"> Sign In with Google</button>
                </div>
                    <div class="col-md-12">
                        <ul class="social-network social-circle">
                            <li><a class="icoFacebook" title="Facebook"><i class="fab fa-facebook-f"></i></a></li>
                            <li><a class="icoTwitter" title="Twitter"><i class="fab fa-twitter"></i></a></li>
                            <li><a class="icoGoogle" title="Google +"><i class="fab fa-google-plus"></i></a></li>
                        </ul>
                    </div>
                </form>
            </div>
        </div>
    </div>

</div>
  </section>
</template>

<script>
import router from '../router'
export default {
  name: 'Login',
  data () {
    return {
      clientId: '265347927468-o28gc2rhncrqiuctu0j9cd3e4t7n4083.apps.googleusercontent.com',
      user: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    login () {
      const payload = {
        email: this.user.email,
        password: this.user.password
      }
      this.$store.dispatch('login', payload)
    },
    OnGoogleAuthSuccess (idToken) {
      this.$store.commit('GOOGLE_LOGIN', idToken)
    },
    OnGoogleAuthFail (error) {
      this.$store.commit('GOOGLEERROR', error)
    },
    toRegister () {
      router.push({ path: '/register' })
    }
  }

}
</script>

<style>
body {
    margin: 0;
    padding: 0;
    font-family: sans-serif;
    background: linear-gradient(to right, #ECBF70, #BDC4C9)
}

.pointer {
    cursor: pointer;
}

.card {
    margin-bottom: 20px;
    border: none
}

.box {
    width: 500px;
    padding: 40px;
    position: absolute;
    top: 50%;
    left: 50%;
    background: #191919;
    ;
    text-align: center;
    transition: 0.25s;
    margin-top: 100px
}

.box input[type="text"],
.box input[type="password"] {
    border: 0;
    background: none;
    display: block;
    margin: 20px auto;
    text-align: center;
    border: 2px solid #3498db;
    padding: 10px 10px;
    width: 250px;
    outline: none;
    color: white;
    border-radius: 24px;
    transition: 0.25s
}

.box h1 {
    color: white;
    text-transform: uppercase;
    font-weight: 500
}

.box input[type="text"]:focus,
.box input[type="password"]:focus {
    width: 300px;
    border-color: #2ecc71
}

.box input[type="submit"] {
    border: 0;
    background: none;
    display: block;
    margin: 20px auto;
    text-align: center;
    border: 2px solid #2ecc71;
    padding: 14px 40px;
    outline: none;
    color: white;
    border-radius: 24px;
    transition: 0.25s;
    cursor: pointer
}

.box input[type="submit"]:hover {
    background: #2ecc71
}

.forgot {
    text-decoration: underline
}

ul.social-network {
    list-style: none;
    display: inline;
    margin-left: 0 !important;
    padding: 0
}

ul.social-network li {
    display: inline;
    margin: 0 5px
}

.social-network a.icoFacebook:hover {
    background-color: #3B5998
}

.social-network a.icoTwitter:hover {
    background-color: #33ccff
}

.social-network a.icoGoogle:hover {
    background-color: #BD3518
}

.social-network a.icoFacebook:hover i,
.social-network a.icoTwitter:hover i,
.social-network a.icoGoogle:hover i {
    color: #fff
}

a.socialIcon:hover,
.socialHoverClass {
    color: #44BCDD
}

.social-circle li a {
    display: inline-block;
    position: relative;
    margin: 0 auto 0 auto;
    border-radius: 50%;
    text-align: center;
    width: 50px;
    height: 50px;
    font-size: 20px
}

.social-circle li i {
    margin: 0;
    line-height: 50px;
    text-align: center
}

.social-circle li a:hover i,
.triggeredHover {
    transform: rotate(360deg);
    transition: all 0.2s
}

.social-circle i {
    color: #fff;
    transition: all 0.8s;
    transition: all 0.8s
}
</style>
