<template>
  <div class="card mx-4">
    <div class="card-header pb-0">
      <h3>UPDATE USER</h3>
    </div>
    <div class="card-body px-3 pt-0 pb-2">
      <div class="mb-3">
      <label for="Email" class="form-label fs-5 text-uppercase font-weight-bolder opacity-7">Email</label>
      <input type="email" class="form-control" id="Email" v-model="email">
      </div>
      <div class="mb-3">
        <label for="Nama" class="form-label fs-5 text-uppercase font-weight-bolder opacity-7">Name</label>
        <input type="text" class="form-control" id="Nama" v-model="name">
      </div>
      <button @click="putUser()" class="btn btn-success">UPDATE</button>
      <div class="mb-3" id="email"></div>
      <div class="mb-3" id="name"></div>
    </div>
  </div>

</template>

<script>
  import axios from 'axios';
  export default{
    data() {
      return{
        email: '',
        name: ''
      }
    },
    methods: {
      async putUser() {
        try{
          const user = await axios.put('https://reqres.in/api/users/2', {
            email: this.email,
            name: this.name
          })

          console.log(user)
          alert('User updated!')
        } catch(e) {
          console.log(e)
        }
        document.getElementById('email').innerHTML = '<label for="email" class="form-label fs-5 text-uppercase font-weight-bolder opacity-7">Email</label><input class="form-control" type="text" value="' + this.email + '" readonly>'
        document.getElementById('name').innerHTML = '<label for="email" class="form-label fs-5 text-uppercase font-weight-bolder opacity-7">Nama</label><input class="form-control" type="text" value="' + this.name + '" readonly>'
    }
  }
}
</script>