<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      <span>userId:{{ userId }}  message:{{ message }}</span>
    </div>
    <router-view/>
  </div>
</template>

<script>
// Component設定
// import InputForm from '@/components/InputForm.vue'

export default {
  name: 'app',
  components: {
    // InputForm
  },
  data() {
    return {
      userId: "",
      message: "" 
    }
  },
  created() {
    const that = this
    liff.init(
      data => {
        that.userId = data.context.userId
        that.message = "初期化できたし"
      }
    )
    .then(() => {
      // start to use LIFF's api
      // initializeApp()
    })
    .catch((err) => {
        // document.getElementById("liffAppContent").classList.add('hidden');
        // document.getElementById("liffInitErrorMessage").classList.remove('hidden');
    })
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
