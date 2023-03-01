<template>
  <tr class="userTable__table-body-row">
    <td class="userTable__table-body-row-column">
      {{ id }}
    </td>

    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uName" />
    </td>
    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uUsername" />
    </td>
    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uEmail" />
    </td>
    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uStreet" />
    </td>
    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uCity" />
    </td>
    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uPhone" />
    </td>
    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uWebsite" />
    </td>
    <td class="userTable__table-body-row-column">
      <input type="text" v-model="uComanyName" />
    </td>

    <td
      class="userTable__table-body-row-column userTable__table-body-row-table-buttons"
    >
      <button
        class="userTable__table-body-row-table-button button__update"
        @click="update(id)"
      >
        Изменить
      </button>
      <button
        class="userTable__table-body-row-table-button button__delete"
        @click="deleteUser(id)"
      >
        Удалить
      </button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "UserItem",

  props: {
    id: {
      type: Number,
    },
    name: {
      type: String,
      default: "No Name",
    },
    username: {
      type: String,
      default: "No Username",
    },
    email: {
      type: String,
      default: "undefield@gmail.com",
    },
    address: {
      type: Object,
    },
    phone: {
      type: String,
    },
    website: {
      type: String,
      default: "google.com",
    },
    company: {
      type: Object,
    },
  },
  data() {
    return {
      uName: "",
      uUsername: "",
      uEmail: "",
      uStreet: "",
      uCity: "",
      uPhone: "",
      uWebsite: "",
      uComanyName: "",
    };
  },
  methods: {
    update(id) {
      this.$emit("update", {
        id: id,
        name: this.uName,
        username: this.uUsername,
        email: this.uEmail,
        street: this.uStreet,
        city: this.uCity,
        phone: this.uPhone,
        website: this.uWebsite,
        companyName: this.uComanyName,
      });
    },
    deleteUser(id) {
      this.$emit("deleteUser", id);
    },
  },
  created() {
    this.uName = this.name;
    this.uUsername = this.username;
    this.uEmail = this.email;
    this.uStreet = this.address.street;
    this.uCity = this.address.city;
    this.uPhone = this.phone;
    this.uWebsite = this.website;
    this.uComanyName = this.company.name;
  },
};
</script>

<style lang="scss" scoped>
.userTable__table-body-row-column input {
  font-size: 12px;
  border: 1px solid #d4d4d4;
  text-align: center;
  margin-left: 2px;
  height: 30px;
  border-radius: 4px;
}
.userTable__table-body-row:last-child {
  border-bottom: 1px;
}
.userTable__table-body-row-table-buttons {
  display: flex;
  flex-direction: column;
}

.userTable__table-body-row-table-button {
  margin: 5px 5px;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  border: none;
}
.button__update {
  background-color: #4caf50;
  color: white;
}

.button__update:hover {
  background-color: #3e8e41;
}

.button__delete {
  background-color: #d12418;
  color: white;
}

.button__delete:hover {
  background-color: #6d1812;
}
</style>
