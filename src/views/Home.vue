<template>
  <div class="home">
    <Navbar />
    <h1 class=" text-4xl text-green-600">KİTAPLAR</h1>

  <section v-if="errored">
    <p>We're sorry, we're not able to retrieve this information at
      the moment, please try back later</p>
  </section>

  <section v-else>
    <div v-if="loading">Loading...</div>

    <div
      v-else
      v-for="book in info"
      class="book"
      v-bind:key="book"
    >
      {{ book.title }}:
      <span class="lighten">
        {{ book.page }}
      </span>
    </div>

  </section>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import Navbar from '@/components/Navbar.vue';
import axios from 'axios';

@Options({
  components: {
    HelloWorld,
    Navbar,
  },
  data() {
    return {
      info: null,
      loading: true,
      errored: false,
    };
  },
  mounted() {
    axios
      .get('http://localhost:1234/books')
      .then((response: any) => {
        this.info = response.data;
      })
      .catch((error: any) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => { this.loading = false; });
  },
})
export default class Home extends Vue {}
</script>
