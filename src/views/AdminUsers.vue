<template>
  <div class="container py-5">
    <!-- AdminNav Component -->
    <AdminNav/>
    <table class="table">
      <thead class="thead-dark">
      <tr>
        <th scope="col">
          #
        </th>
        <th scope="col">
          Email
        </th>
        <th scope="col">
          Roles
        </th>
        <th
            scope="col"
            width="140"
        >
          Action
        </th>
      </tr>
      </thead>
      <tbody>
      <tr
          v-for="user in users"
          :key="user.id"
      >
        <th scope="row">
          {{ user.id }}
        </th>
        <td>
          {{ user.name }}
        </td>
        <td  v-if="user.isAdmin">
          admin
        </td>
        <td v-else>
          user
        </td>
        <td>
          <button
              v-if="user.id !== currentUser.id"
              type="button"
              class="btn btn-link"
              @click.stop.prevent="toggleUserRole(user.id)"
          >
            <template v-if="user.isAdmin">set as user</template>
            <template v-else>set as admin</template>
          </button>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import AdminNav from '@/components/AdminNav'

const dummyData = {
  "users": [
    {
      "id": 1,
      "name": "root",
      "email": "root@example.com",
      "password": "$2a$10$yv/782.F1b2zPoCQ4h/uAOzjSOLFJYB8r6Yjg5NthpcoyeolTUYWC",
      "isAdmin": true,
      "image": null,
      "createdAt": "2022-03-16T05:48:21.000Z",
      "updatedAt": "2022-03-16T05:48:21.000Z"
    },
    {
      "id": 2,
      "name": "user1",
      "email": "user1@example.com",
      "password": "$2a$10$Lon.L2e26Lp/Vzq99wMbPuJByVs.QGXI.QBuh90JJVDBSdcX6qthO",
      "isAdmin": false,
      "image": null,
      "createdAt": "2022-03-16T05:48:21.000Z",
      "updatedAt": "2022-03-16T05:48:21.000Z"
    },
    {
      "id": 3,
      "name": "user2",
      "email": "user2@example.com",
      "password": "$2a$10$u5FV77ig5/AyIiz8ogqiG.GrjGxvmEkYzvKtLBQEFWG1CGj5zhD3.",
      "isAdmin": false,
      "image": null,
      "createdAt": "2022-03-16T05:48:21.000Z",
      "updatedAt": "2022-03-16T05:48:21.000Z"
    }
  ]
}
export default {
  name: "AdminUsers",
  components: {
    AdminNav
  },
  data() {
    return {
      users: [],
      currentUser: {
        "id": 5
      }
    }
  },
  created() {
    this.fetchUsers()
  },
  methods: {
    fetchUsers() {
      this.users = dummyData.users
    },
    toggleUserRole(userId) {
      this.users = this.users.map(user => {
        if (user.id === userId) {
          return {
            ...user,
            isAdmin: !user.isAdmin
          }
        }
        return user
      })
    }
  }
}

</script>

<style scoped>

</style>