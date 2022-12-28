<template>
  
    <div class="login">
        <label>Username</label>
        <input type="email" placeholder="email address" v-bind:value="value" 
         @focus="clearPlaceholder" />
        <label>Password</label>
        <input type="password" placeholder="Password" v-bind:value="value"  @focus="clearPlaceholder" />
        <button class="btn" @click="login">Login   
  </button>
    </div>
    
</template>

<script>
export default {
  name: 'SideLogin',
  components: {
    
  },
  data() {
      return {
        value:''
      }
    },
    methods: {
    async login() {
        try {
        // Make API call to verify login credentials
        const user = await window.api.login(this.email, this.password)
        // Store user information in global state
        this.$store.commit('setUser', user)
        // Navigate to HomePage component
        this.$router.push({ path: './PosFront.vue' })
        } catch (error) {
        // Handle login error
        alert('not authorized');
        }
    }
      
    },
    clearPlaceholder() {
      this.value = '';
    }
}


</script>
<style scoped>  
.login {
  position: relative;
  top: 0;
  right: 0;
  width: 250px;
  height: 200px;
  background: rgb(221, 231, 236);
  padding: 20px;
  box-sizing: border-box;
  margin-left:180px;
}
.btn {
  position: relative;
  top: 5px;
  right: 0;
  width: 80px;
  height: 40px;
  background: rgb(18, 13, 13);
  color: rgba(243, 235, 235, 0.845);
  border: 1px solid goldenrod;
}
label {
  color: rgba(5, 69, 33, 0.845);
  font-size: small;
}
</style>