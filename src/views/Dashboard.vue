<template>
  <div>
    <h1>Welcome to our Dashboard Page</h1>
    <button @click.prevent="signOut">Sign out</button>
    <p>Welcome: {{ userEmail }}</p>
  </div>
</template>

<script>
import { useStore } from "vuex";
import { computed } from "vue";
export default {
  setup() {
    //create store instance
    const store = useStore();
    // Fetches email of logged in user from state
    const userEmail = computed(() => store.state.user);
     const signOut = () => {
      // dispatch the sign out action to log user out
      store.dispatch("signOutAction");
    };
    return {
      signOut,
      userEmail,
    };
  },
};
</script>