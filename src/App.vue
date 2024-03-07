<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <!-- templateRefs instead of queryselector -->
  <!-- <input type="text" ref="name"> -->
  <!-- <button @click="handleClick">click here</button> -->
  
  <!-- Adding props to child component -->
  <!-- <modalScrn heading="sign up for Vhighc Enterprise" text="Grab your opportunity now"/> -->
  
  <!-- Data Binding -->
  <!-- <modalScrn :heading="heading" :text="text" theme="short"/> -->
  
  <!-- Listening to emitted(close) Custom Events from the child(Modal) component -->
  <!-- <div v-if="showModal"> -->

    <!-- Using teleport -->
  <teleport to="#modals" v-if="showModal">
    <!-- <modalScrn @close="toggleModal" :heading="heading" :text="text" theme="short"/> -->
    
    <!-- Slots -->
    <modalScrn @close="toggleModal" theme="short">
      <!-- named slots -->
      <template v-slot:links>
        <a href=''>sign up today</a>
        <a href=''>see more</a>
      </template>
      
      <!-- default slots -->
      <h1>sign up for Vhighc Enterprise</h1>
      <p>Grab your opportunity now</p>
    </modalScrn>
  <!-- </div> -->

  <!-- Using teleport -->
</teleport>

  <!-- New modal -->
  <!-- <div v-if="showModalTwo"> -->

    <!-- Using teleport -->
    <teleport to="#modals" v-if="showModalTwo">
    <modalScrn @close="toggleModalTwo">      
      <h1>sign up for more update</h1>
      <p>Get more promo codes</p>
    </modalScrn>
  <!-- </div> -->

  <!-- Using teleport -->
  </teleport>

  <!-- Added an event modifier(.alt, .shift, .right) -->
  <button @click.alt="toggleModal">open modal (alt)</button>
  
  <!-- New modal -->
  <button @click="toggleModalTwo">open second modal</button>
</template>

<script>
import modalScrn from "./components/Modal.vue"

export default {
  name: 'App',
  components: {modalScrn},
  data() {
    return{
      title: "Vhighc First Vue App :)",
      
      // Data Binding
      // heading: "sign up for Vhighc Enterprise",
      // text: "Grab your opportunity now", 
      
      // Emitting Custom Events
      showModal: false,

      // New modal
      showModalTwo: false
    }
  },
  
  methods: {
    // templateRefs instead of queryselector
    // handleClick () {
    //   console.log(this.$refs.name)
    //   this.$refs.name.classList.add('active')
    //   this.$refs.name.focus()  
    // },

    // Emitting Custom Events
    toggleModal() {
      this.showModal = !this.showModal
    },

    // New modal
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
/* Teleport style modified */
#app, #modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* #app{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
  /* modal style clash */
  color: blueviolet;
}
</style>
