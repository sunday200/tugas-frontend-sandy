<template>
  <div class="card mx-4">
    <div class="card-header pb-0">
      <h3>USERS</h3>
    </div>
    <div class="card-body px-0 pt-0 pb-2">
      <div class="table-responsive p-0">
        <table class="table align-items-center mb-0">
          <thead>
            <tr>
              <th class="text-uppercase text-secondary font-weight-bolder opacity-7 fs-4">Photo</th>
              <th class="text-uppercase text-secondary font-weight-bolder opacity-7 fs-4">First Name</th>
              <th class="text-uppercase text-secondary font-weight-bolder opacity-7 fs-4">Last Name</th>
              <th class="text-uppercase text-secondary font-weight-bolder opacity-7 fs-4">Email</th>
            </tr>
          </thead>
          <tbody v-if="getUser && getUser.length">
            <tr v-for="getUser of getUser">
              <td>
                <div>
                  <img :src=getUser.avatar class="avatar avatar-xxl ms-2 rounded-circle"/>
                </div>
              </td>
              <td>
                <div class="d-flex px-2 py-1">
                  <div class="d-flex flex-column justify-content-center">
                    <h6 class="mb-0">{{getUser.first_name}}</h6>
                  </div>
                </div>
              </td>
              <td>
                <div class="d-flex px-2 py-1">
                  <div class="d-flex flex-column justify-content-center">
                    <h6 class="mb-0">{{getUser.last_name}}</h6>
                  </div>
                </div>
              </td>
              <td>
                <div class="d-flex px-2 py-1">
                  <div class="d-flex flex-column justify-content-center">
                    <h6 class="mb-0">{{getUser.email}}</h6>
                  </div>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: "authors-table",
    data() {
      return {
        getUser: []
      }
    },
    created() {
      axios.get('https://reqres.in/api/users')
        .then(response => {
          this.getUser = response.data.data
        })
    }
  };
</script>