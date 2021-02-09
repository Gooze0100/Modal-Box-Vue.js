<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" >
  <button @click="handleClick">Click me</button>
  <p>Welcome...</p>
  <!-- nested -->
  <!-- reikia -binf jei nori kad butu array, boolean ir ne tekstas -->
  <!-- <Modal header="Sign up for the Giveaway" text="Grab your ninja swag for half price!"/> -->
  <!-- theme galima su props padaryti jei toks ir toks tada kazka pakeisti -->
  <div v-if="showModal">
  <Modal :header="header" :text="text" theme="sale" @close="toggleModal" />
  </div>
  <button @click.alt="toggleModal">Open Modal (alt)</button>
</template>

<script>
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First vue App :)',
      header: 'Sing up for the Giveaway!',
      text: 'Grab your ninja swag for half price!',
      showModal: false,
      }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      // $refs yra tas pats kas querySelector, todel reikia nurodyti refs prie elementu
      // su $refs galima juos pasiekti visa DOM
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
    },

    toggleModal() {
      // iskviesti galima tik su this nes imi is vidaus
      this.showModal = !this.showModal;
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
