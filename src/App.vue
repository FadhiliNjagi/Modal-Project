<template>
  <div>
      <h1>{{ greeting }}</h1><br>
      <button @click="toggleModal">Show Modal</button>
      <button @click="toggleModal2">Show Modal 2</button>
      <teleport to=".modals" v-if="showModal">
          <Modal theme="salefgf" @close="toggleModal">
              <h1>Sale! Sale! Sale!</h1>
              <p>Don't miss out on the sale</p>
              <template v-slot:links>
                  <a href="#">Sign Up</a>
                  <a href="#">Log in</a>
                  <a href="#">About Us</a>
              </template>
          </Modal>
      </teleport>
      <div v-if="showModal2">
          <Modal @close="toggleModal2">
              <h1>Modal 2 Successfully Created</h1>
              <p>Hooray! Cheers to us</p>
          </Modal>
      </div>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
        greeting: 'My First Vue App',
        header: "Subscribe to our newsletter!",
        text: "Lots of awesome content every week",
        showModal: false,
        showModal2: false
    }
  },
  methods: {
      handleClick() {
          console.log(this.$refs.name)
          this.$refs.name.classList.add('active')
      },
      toggleModal() {
          this.showModal = !this.showModal
      },
      toggleModal2(){
          this.showModal2 = !this.showModal2
      }
  },
}
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
</style>
