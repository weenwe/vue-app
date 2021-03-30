<template>
  <div id="app">
    <div class="container">
      <h1 class="mb-4">Daftar Pelanggan</h1>
      <hr>
      <p> 
        <button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
        Tambah Pelanggan
        </button>
      </p>

      <customer-table 
        v-bind:customers='customers' 
        @edit-customer="editCustomer"
        @delete-customer="deleteCustomer"
      />

      <div class="collapse" id="collapseExample">
        <div class="card card-body">
          <h2>Input Data Pelanggan</h2>
          <hr>

          <!-- <customer-form @add-customer="addCustomer"/> -->
          <customer-form @add-customer="addCustomer"/>

        </div>
      </div>
    </div>
  </div>
</template>


<script>
import CustomerTable from '@/components/CustomerTable.vue'
import CustomerForm from '@/components/CustomerForm.vue'

export default {
  name: 'App',
  components: {
    CustomerTable,
    CustomerForm, 
  },
  data() {
    return {
      customers: [
        {
          id: 1,
          name: 'Bambang',
          email: 'bambang@mail.com',
          address: 'Jl.Kenanga',
        },
        {
          id: 2,
          name: 'Dika',
          email: 'dika@mail.com',
          address: 'Jl.Mangga',
        },
        {
          id: 3,
          name: 'Agus',
          email: 'agus@mail.com',
          address: 'Jl.Mataram',
        },
      ],
    }
  },
  methods: {
    addCustomer(customer) {
      this.customers.push(customer);
    },
    editCustomer(id, data) {
      this.customers = this.customers.map(function (customer) { 
        return customer.id === id ? data : customer;
      });
    },
    deleteCustomer(id) {
      this.customers = this.customers.filter(function (customer) { 
        return customer.id !== id;
      });
    }
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
