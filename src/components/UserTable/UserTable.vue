<template>
  <div class="userTable">
    <table class="userTable__table">
      <thead class="userTable__table-head">
        <tr class="userTable__table-head-row">
          <th class="userTable__table-head-row-column">Id</th>
          <th class="userTable__table-head-row-column">Name</th>
          <th class="userTable__table-head-row-column">Username</th>
          <th class="userTable__table-head-row-column">Email</th>
          <th class="userTable__table-head-row-column">Street</th>
          <th class="userTable__table-head-row-column">City</th>
          <th class="userTable__table-head-row-column">Phone</th>
          <th class="userTable__table-head-row-column">Website</th>
          <th class="userTable__table-head-row-column">Company</th>
          <th class="userTable__table-head-row-column">Active</th>
        </tr>
      </thead>
      <tbody class="userTable__table-body">
        <UserItem
          v-for="(item, index) in users"
          :key="item.id"
          :id="index"
          :name="item.name"
          :username="item.username"
          :email="item.email"
          :address="item.address"
          :phone="item.phone"
          :website="item.website"
          :company="item.company"
          @update="update"
          @deleteUser="deleteUser"
        />
      </tbody>
    </table>

    <!-- <button @click="cons">click</button> -->
  </div>
</template>

<script>
import UserItem from './User/User.vue';
export default {
  name: 'UserTable',
  components: { UserItem },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    cons() {
      console.log(this.users);
    },
    update(data) {
      this.users[data.id].name = data.name;
      this.users[data.id].username = data.username;
      this.users[data.id].email = data.email;
      this.users[data.id].address.street = data.street;
      this.users[data.id].address.city = data.city;
      this.users[data.id].phone = data.phone;
      this.users[data.id].website = data.website;
      this.users[data.id].company.name = data.companyName;
    },
    deleteUser(index) {
      console.log(index);

      this.users.splice(index, 1);
    },
  },
  created() {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then((response) => response.json())
      .then((json) => (this.users = json));
  },
};
</script>

<style lang="scss" scoped>
.userTable__table {
  width: 100%;
  border-collapse: collapse;
  text-align: center;
}
.userTable__table-head {
  background-color: #ffffff;
}
.userTable__table-body:nth-child(2n) {
  background-color: #f2f2f2;
}

.userTable__table-head-row-column {
  border: 1px solid rgb(192, 192, 192);
  padding: 8px;
}

@media screen and (max-width: 768px) {
  .userTable__table-head-row {
    display: none;
  }

  .userTable__table-body-row {
    display: block;
    margin-bottom: 10px;
    border: 1px solid #ddd;
  }
}
</style>
