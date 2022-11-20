<!-- src/views/SignIn.vue -->
<template>
  <div>
      <h1>Login Page</h1>
      <form @submit.prevent="signIn">
        <input
          class="inputField"
          type="email"
          placeholder="Your email"
          v-model="form.email"
        />
        <input
          class="inputField"
          type="password"
          placeholder="Your Password"
          v-model="form.password"
        />
        <button type="submit">Sign In</button>
      </form>
      <p>
        Don't have an account? 
        <router-link to="/sign-up">Sign Up</router-link>
      </p>
    </div>
</template>

<script>
import { reactive } from "vue";
import { useStore } from "vuex";
export default {
  setup() {
    // wrap data gotten from form input in vue's reactive object
    const form = reactive({
      email: "",
      password: "",
    });
    //create new store instance
    const store = useStore();
    const signUp = () => {
      // dispatch the sign in action to Log in the user
      store.dispatch("signInAction", form);
    };
    return {
      form,
      signIn,
    };
  },
};
</script>