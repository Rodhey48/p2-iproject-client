<template>
  <!-- ini login -->
  <div class="container">
    <div class="row justify-content-center pt-5">
      <section class="section col-9" id="loginpage">
        <div class="card" style="margin-left: 25%; margin-right: 25%">
          <div
            class="card-title mx-auto"
            style="font-size: x-large; font-weight: bold"
          >
            Login
          </div>
          <div class="card-body">
            <form action="" id="login-form">
              <div class="mb-3">
                <label for="formName" class="form-label">Email : </label>
                <input
                  type="text"
                  class="form-control"
                  id="loginname"
                  placeholder="Email"
                  v-model="formlogin.email"
                />
              </div>
              <div class="mb-3">
                <label for="Password" class="form-label">Password : </label>
                <input
                  type="password"
                  class="form-control"
                  id="loginpassword"
                  placeholder="Password"
                  v-model="formlogin.password"
                />
              </div>
              <div class="col-12">
                <button
                  style="margin-left: 40%; margin-right: 30%"
                  type="submit"
                  class="btn btn-primary"
                  @click.prevent="login"
                >
                  Login</button
                ><br />
              </div>
              <br />
            </form>
            <label for="">Login With Google</label><br />

            <div class="col-12 text-end">
              <p>
                you need sign up?
                <button
                  class="btn btn-primary button-signin"
                  id="button-signin"
                  @click.prevent="toRegister"
                >
                  Sign Up
                </button>
              </p>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";

export default {
  components: {},
  name: "login",
  data() {
    return {
      formlogin: {
        email: "",
        password: "",
      },
      params: {
        client_id:
          "122937689900-o79frcuqpo9h9vva90mnr9ebpvsvtebm.apps.googleusercontent.com",
      },
      renderParams: {
        width: 250,
        height: 50,
        longtitle: true,
      },
    };
  },
  computed: {
    ...mapState(["isLogin"]),
  },
  methods: {
    ...mapActions(["postLogin", "loginWithGoogle"]),
    async login() {
      await this.postLogin(this.formlogin);
      if (this.isLogin) {
        this.$router.push({ name: "Home" });
      }
    },
    toRegister() {
      this.$router.push({ name: "register" });
    },
    async onSuccess(googleUser) {
      try {
        console.log(googleUser.getAuthResponse().id_token);
        console.log("Testing");
        let idToken = googleUser.getAuthResponse().id_token;
        console.log(idToken);
        this.loginWithGoogle(idToken);
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style>
</style>