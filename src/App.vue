<template>
  <h1>{{ title }}</h1>

  <input type="text" ref="text">
  <button @click="handleClick">Change text color</button>
  <section class="modalContent">
    <div v-if="showModal">
      <!-- <Modal titre="Vous n'êtes pas connecté :/" :text="text" theme="sale" @EcloseModale="toggleModale" />  props-->
      <Modal theme="sale" @EcloseModale="toggleModale">
        <template v-slot:links>
          <a href="#">Sign up</a>
          <a href="#">more infos</a>
        </template>
        <h1>Abonne toi !</h1>
        <p>il est nécessaire de s'abonner pour réailiser cette action</p>
      </Modal>
      
    </div>
    <div v-if="showLogInModal">
      <LogInModal theme="black" @EcloseScndModale="toggleLogInModal">
        <h1>Se connecter</h1>
        <input type="text">
        <input type="text">
        <template v-slot:links>
          <a href="#">se connecter</a>
        </template>
      </LogInModal>
    </div>

    <h1>I've created some modals</h1>
    <button @click="toggleModale">
      open sign up modal
    </button>
    <button @click="toggleLogInModal">
      open other modal
    </button>
  </section>
  <p></p>
    
  
</template>

<script>
import Modal from './components/Modal.vue' 
import LogInModal from './components/SecondModal.vue'

export default {
  name: 'App',
  data () {
    return{
      title: "My first vue app",
      text: "créez un compte en quelques secondes seulement ! et profitez de nombreux avantages",
      showModal: false,
      showLogInModal: false
    }
  },
  components: {
    Modal,
    LogInModal
  },
  methods: {
    handleClick(){
      this.$refs.text.classList.add("active")
      this.$refs.text.focus()
    },
    toggleModale() {
      this.showModal = !this.showModal
    },
    toggleLogInModal(){
      this.showLogInModal = !this.showLogInModal
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
.active{
  color: aqua;
}
h1{
  font-size: 30px;
  color:darkblue;
  margin: 0;
}
.modalContent{
  width: 75vw;
  padding: 10px;
  margin: 20px auto;
  background: rgb(245, 245, 245);
  text-align: left;
}
.modalContent button{
  display: block;
  margin: 0 auto;
  
}
</style>
