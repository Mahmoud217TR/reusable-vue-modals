<template>
  <img class="opener" alt="Vue logo" src="./assets/logo.png" @click="toggleModal">
  <Modal title ='Modal Message'
         msg ='Lorem ipsum dolor sit amet, consectetur adipisicing elit. Animi, iure deleniti totam, veniam obcaecati fugit magnam officia soluta voluptas, neque explicabo sapiente maiores enim a dolorum. Id, cupiditate quaerat nisi, dolor blanditiis expedita consectetur unde, necessitatibus numquam officiis cum itaque!'
         :show='showModal'
         @close='toggleModal'
         buttons="Accept,Later,Cancel"
         @Accept="buttonClicked('accepted')"
         @Later="buttonClicked('later')"
         @Cancel="buttonClicked('cancled')"
         />
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      showModal: false,
    }
  },
  methods: {
    toggleModal(){
      this.showModal = !this.showModal
    },
    buttonClicked(num){
      console.log(num)
    }
  },
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
.opener{
  cursor: pointer;
}
</style>
