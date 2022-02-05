<template>
  <div v-bind:class="'user__container'">
    <h1>Random User Generator</h1>
    <img :class="gender" :src="image" alt="">
    <h2> {{firstName}} {{lastName}} </h2>
    <h2>Email : {{email}} </h2>
    <button
      :class="gender"
      @click="getUser"
    >
      Get Random User
    </button>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data(){
      return{
        firstName : "Ishan",
        lastName : "Bhardwaj",
        email : "theishanbh@gmail.com",
        gender : "male",
        image : "https://randomuser.me/api/portraits/women/10.jpg"
      }
    },
    methods : {
      async getUser() {
        const res = await fetch('https://randomuser.me/api')
        const results = await res.json()
        const person = results.results[0]
        console.log(person);
        this.firstName = person.name.first
        this.lastName = person.name.last
        this.gender = person.gender
        this.email = person.email
        this.image = person.picture.large
      }
    }
  }
</script>

<style>
.user__container{
  width: 100%;
  text-align: center;
}

img{
  border-radius: 50%;
  border: 5px solid;
  margin-bottom:  1rem;
}

.male{
  border-color: steelblue;
  background-color: steelblue;
}

.female{
  border-color: pink;
  background-color: pink;
  color: #333
}

button{
  background-color: #333; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
}

</style>
