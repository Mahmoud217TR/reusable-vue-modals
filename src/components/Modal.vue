<template>
  <div class="back-drop" @click.self="close" v-if="show">
    <div class="modal">
      <div class="x-button" @click="close"></div>
      <h1>{{ title }}</h1>
      <p>{{ msg }}</p>
      <div class="actions">
        <button class="button" v-for="bt in buttonsArray" @click="buttonClicked(bt)">{{ bt }}</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: ['title','msg','show','buttons'],
  data() {
    return {
      buttonsArray: [],
    }
  },
  methods: {
    close(){
      this.$emit('close')
    },
    buttonClicked(buttonText){
      this.$emit(buttonText)
      this.close()
    }
  },
  mounted() {
    this.buttonsArray = this.buttons.split(',')
  },
}
</script>

<style scoped>
  .back-drop{
    z-index: 100;
    background: rgba(0, 0, 0, 0.5);
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    overflow: scroll;
  }

  .back-drop::-webkit-scrollbar {
    display: none;
  }

  .modal{
    position: relative;
    text-align: center;
    background: #fff;
    width: max(50%,15rem);
    padding: 2rem 2rem;
    margin: 2rem auto;
    border-radius: .25rem;
    z-index: 101;
  }

  .x-button::after{
    content: "\00d7";
    font-size: 2rem;
    position: absolute;
    top: 0;
    right: .5rem;
    cursor: pointer;
  }

  .actions{
    margin-top: 2rem;
    display: block;
  }

  .button{
    background-color: #fff;
    padding: .5rem 1rem;
    border: solid .15rem #ddd;
    border-radius: .25rem;
    cursor: pointer;
    width: clamp(4rem,30vw,8rem);
    font-weight: bold;
    text-align: center;
    color: #2c3e50;
    overflow: hidden;
    margin: 1rem;
  }

  .button:focus,button:focus-visible{
   box-shadow: 0 0 0 .125rem #ddd; 
   outline: none;
  }
</style>
