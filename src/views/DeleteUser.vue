<template>
  <div class="card mx-4">
    <div class="card-header pb-0 mb-2">
      <h3>DELETE USER</h3>
    </div>
    <div class="card-body px-3 pt-0 pb-2 ms-2">
      <button @click='deleteUser()' class="btn btn-success">DELETE</button>
    </div>
  </div>

</template>

<script>
  import axios from 'axios';
  export default{
    methods: {
      async deleteUser() {

        let x = window.confirm('You want to delete user?')

        if(x){
          const user = await axios.delete('https://reqres.in/api/users/2')
          console.log(user)
          alert('User deleted!')
        }
    }
  }
}
</script>