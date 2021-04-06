<template>
  <div class="login">
      <Navbar />
      <h1>This is a login page</h1>
  </div>
</template>

<script>
import { Options, Vue } from 'vue-class-component';
import Navbar from '@/components/Navbar.vue';

@Options({
  components: {
    Navbar,
  },
})

export default class Login extends Vue {}
</script>

<style>

</style>
