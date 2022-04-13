<template>
  <div class="container">
    <div class="rectangleLeft"></div>
    <div class="rectangleRight"></div>

    <form @submit.prevent="checkForm">
      <div class="form-block">
        <div class="h1">Create an account</div>
        <div>
          <p
            class="errForm"
            v-if="$v.form.login.$dirty && !$v.form.login.required"
          >
            This is required
          </p>
          <p
            class="errForm"
            v-if="$v.form.login.$dirty && !$v.form.login.minLength"
          >
            Login is too short
          </p>
          <input
            class="logInput"
            placeholder="Login"
            :class="$v.form.login.$error ? 'is-invalid' : ''"
            v-model.trim="form.login"
          />
        </div>

        <div>
          <p
            class="errForm"
            v-if="$v.form.login.$dirty && !$v.form.password.required"
          >
            This is required
          </p>
          <input
            class="passInput"
            type="password"
            placeholder="Password"
            v-model.trim="form.password"
            :class="$v.form.login.$error ? 'is-invalid' : ''"
          />
        </div>

        <div>
          <p
            class="errForm"
            v-if="$v.form.login.$dirty && !$v.form.email.required"
          >
            This is required
          </p>
          <p
            class="errForm"
            v-if="$v.form.login.$dirty && !$v.form.email.email"
          >
            Email is invalid
          </p>
          <input
            class="emailInput"
            type="email"
            placeholder="Email"
            v-model.trim="form.email"
            :class="$v.form.login.$error ? 'is-invalid' : ''"
          />
        </div>

        <div>
          <button><p class="btn-text">Sign up</p></button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import { validationMixin } from 'vuelidate';
import { required, minLength, email } from 'vuelidate/lib/validators';
export default {
  mixins: [validationMixin],
  data() {
    return {
      form: {
        login: '',
        password: '',
        email: '',
      },
    };
  },
  validations: {
    form: {
      login: { required, minLength: minLength(5) },
      password: { required },
      email: { required, email },
    },
  },
  methods: {
    checkForm() {
      this.$v.form.$touch();
      if (!this.$v.form.$error) {
        console.log('successful validation');
      }
    },
  },
};
</script>

<style>
body,
html {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

.errForm {
  color: red;
  text-align: center;
  margin-bottom: 1px;
  margin-top: -11px;
  font-size: 17px;
}

.container {
  display: flex;
  flex-flow: column nowrap;
  max-width: 1920px;
  height: 1080px;

  background: #a7d7c5;
}

.form-block {
  position: absolute;
  width: 698px;
  height: 698px;
  left: 611px;
  top: 191px;

  background: #f6fbf9;
  border-radius: 49.0901px;
}

.h1 {
  margin-top: 67.5px;
  margin-bottom: 73px;
  margin-left: 107.38px;

  width: 483.23px;
  height: 72.1px;

  font-style: normal;
  font-weight: 700;
  font-size: 55.2264px;
  line-height: 72px;

  text-align: center;

  color: #212b27;
}

.logInput {
  width: 575.27px;
  height: 84.37px;

  margin-bottom: 23.01px;
  margin-left: 59.83px;

  background: #ffffff;
  border: 1.53407px solid rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  border-radius: 15.3407px;
}

.passInput {
  width: 575.27px;
  height: 84.37px;

  margin-left: 59.83px;
  margin-bottom: 23.01px;

  background: #ffffff;
  border: 1.53407px solid rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  border-radius: 15.3407px;
}

.emailInput {
  width: 575.27px;
  height: 84.37px;

  margin-left: 59.83px;

  background: #ffffff;
  border: 1.53407px solid rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  border-radius: 15.3407px;
}

input {
  font-size: 25px;
}

::placeholder {
  font-family: 'Karla';
  font-style: normal;
  font-weight: 400;
  font-size: 25px;
  text-align: center;

  color: rgba(0, 0, 0, 0.5);
}

button {
  width: 391.19px;
  height: 90.51px;

  margin-left: 153.41px;
  margin-top: 32.22px;

  background: #84c7ae;
  border-radius: 23.011px;
}

.btn-text {
  margin-top: 23.01px;

  font-family: 'Karla';
  font-style: normal;
  font-weight: 700;
  font-size: 35px;

  text-align: center;

  color: #ffffff;
}

.rectangleLeft {
  width: 550px;
  height: 550px;

  background: #c1e3d6;
  border-radius: 161px;
  transform: rotate(-45deg);
}

.rectangleRight {
  width: 550px;
  height: 550px;

  background: #c1e3d6;
  border-radius: 161px;
  transform: rotate(-5deg);
  margin-left: 1311px;
  margin-bottom: 95px;
}
</style>
