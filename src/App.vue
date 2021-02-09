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
    <!-- props naudojam -->
  <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
  <!-- <Modal theme="sale" @close="toggleModal"> -->
  <Modal theme="" @close="toggleModal">
    <!-- naudojam slots -->
    <h1>Ninja Givaway!</h1>
    <p>Grab your ninja swag for half price</p>

    <!-- tai sukuriamas name to slot -->
    <template v-slot:links>
    <!-- named slots iyra irasomi viduje template taip sukuriasi names slots -->
    <a href="#">Sing up now</a>
    <a href="#">more info</a>
    </template>
  </Modal>
  </div>

<!-- second modal box -->
  <!-- <div v-if="showModalTwo">
  <Modal theme="sale" @close="toggleModalTwo">
    <h1>Sign up to the newsletter</h1>
    <p>Fro updates and promo codes!</p>
  </Modal>
  </div> -->

<!-- second modal box -->
<!-- teleportuoja kur reikia pagal kalse -->
  <teleport to='.modals' v-if="showModalTwo">
  <Modal theme="sale" @close="toggleModalTwo">
    <h1>Sign up to the newsletter</h1>
    <p>Fro updates and promo codes!</p>
  </Modal>
  </teleport>

  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <!-- second modal box -->
  <button @click="toggleModalTwo">Open Modal</button>
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
      showModalTwo: false,
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
    },

    toggleModalTwo() {
      // iskviesti galima tik su this nes imi is vidaus
      this.showModalTwo = !this.showModalTwo;
    },

  }
}


// challenge
//  - create an extra button to open a different modal
//  - use the same modal component but pass in a different template
//  - use a different method (e.g. toggleModalTwo) and data (e.g. showModalTwo)

</script>

<style>
#app, .modals {
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
