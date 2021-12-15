<template>
  <div class="container">
    <div class="row justify-content-center pt-5">
      <section class="section col-9" id="registerpage">
        <div class="card" style="margin-left: 25%; margin-right: 25%">
          <div
            class="card-title mx-auto"
            style="
              font-size: x-large;
              font-weight: bold;
              margin-left: 30%;
              margin-right: 30%;
            "
          >
            Register
          </div>
          <div class="card-body">
            <form action="">
              <div class="mb-3">
                <label for="form Name" class="form-label">Name : </label>
                <input
                  type="text"
                  class="form-control"
                  id="formname"
                  placeholder="Username"
                  v-model="formRegister.name"
                />
              </div>
              <div class="mb-3">
                <label for="form position" class="form-label"
                  >Position :
                </label>
                <input
                  type="text"
                  class="form-control"
                  id="formname"
                  placeholder="position"
                  v-model="formRegister.name"
                />
              </div>
              <div class="mb-3">
                <label for="form phoneNumber" class="form-label"
                  >Phone Number :
                </label>
                <input
                  type="text"
                  class="form-control"
                  id="formname"
                  placeholder="phoneNumber"
                  v-model="formRegister.name"
                />
              </div>
              <div class="mb-3">
                <label for="form email" class="form-label">Email : </label>
                <input
                  type="text"
                  class="form-control"
                  id="formemail"
                  placeholder="Email"
                  v-model="formRegister.email"
                />
              </div>
              <div class="mb-3">
                <label for="Password" class="form-label">Password : </label>
                <input
                  type="password"
                  class="form-control"
                  id="formpassword"
                  placeholder="Password"
                  v-model="formRegister.password"
                />
              </div>
              <div class="col-12">
                <button
                  style="margin-left: 35%; margin-right: 30%"
                  type="submit"
                  id="button-register"
                  class="btn btn-primary mx-auto"
                  @click.prevent="register"
                >
                  register
                </button>
              </div>
            </form>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
export default {
  name: "register",
  data() {
    return {
      formRegister: {
        name: "",
        email: "",
        password: "",
      },
    };
  },
  computed: {
    ...mapState(["isRegister"]),
  },
  methods: {
    ...mapActions(["postRegister"]),
    async register() {
      await this.postRegister(this.formRegister);
      if (this.isRegister) {
        this.$router.push({ name: "login" });
      }
    },
  },
};
</script>

<style>
</style>