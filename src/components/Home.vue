<template>
  <div className="form">
    <form @submit="handleSubmit">
      <div>
        <p>Email</p>
        <input type="email" placeholder="abc@daksh.com" required v-model="input.email">
      </div>
      <div>
        <p>Password</p>
        <input type="password" placeholder="password" required v-model="input.password"/>
      </div>
      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
import router from '@/router';

export default {
  name: 'HomePage',
  data(){
    return {
      input:{
        email:"",
        password:""
      }
    }
  },
  
  methods:{
    handleSubmit(e){
      e.preventDefault();
      console.log(this.input.email, this.input.password);
      router.push({path:'dashboard'})
    }
  }

  }
</script>

<style scoped>
.form{
  margin:2rem auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  border:5px solid aliceblue;
  width:20%;
  padding:1rem;
  background-color: antiquewhite;
}
div p{
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
  font-weight: 400;
}
div input{
  padding:0.5rem;
  border-radius: 25px;
  margin-bottom: 1rem;
  font-size: 1rem;
}
div button{
  background: black;
  color:white;
  border-radius: 25px;
  align-items: center;
  text-align: center;
  padding:0.5rem;
  width:100%;
  text-transform: uppercase;
  cursor:pointer;
}

</style>
