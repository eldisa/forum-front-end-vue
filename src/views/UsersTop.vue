// ./src/views/UsersTop.vue
<template>
  <div class="container py-5">
    <NavTabs/>
    <h1 class="mt-5">
      美食達人
    </h1>
    <hr>
    <div class="row text-center">
      <div
          v-for="user in users"
          :key="user.id"
          class="col-3"
      >
        <router-link :to="{ name: 'user', params: { id: user.id } }">
          <img
              :src="user.image | emptyImage"
              width="140px"
              height="140px"
          >
        </router-link>
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary">追蹤人數：{{ user.FollowerCount }}</span>
        <p class="mt-3">
          <button
              v-if="user.isFollowed"
              type="button"
              class="btn btn-danger"
              @click.stop.prevent="deleteFollowing(user.id)"
          >
            取消追蹤
          </button>
          <button
              v-else
              type="button"
              class="btn btn-primary"
              @click.stop.prevent="addFollowing(user.id)"
          >
            追蹤
          </button>
        </p>
      </div>
    </div>
  </div>
</template>
<script>
import NavTabs from "../components/NavTabs";
import {emptyImageFilter} from './../utils/mixins'
const dummyData =
    {
      "users": [
        {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z",
          "Followers": [
            {
              "id": 1,
              "name": "root",
              "email": "root@example.com",
              "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
              "isAdmin": false,
              "image": null,
              "createdAt": "2021-10-19T09:35:54.000Z",
              "updatedAt": "2021-10-27T05:23:52.000Z",
              "Followship": {
                "followerId": 1,
                "followingId": 2,
                "createdAt": "2022-01-08T13:53:28.000Z",
                "updatedAt": "2022-01-08T13:53:28.000Z"
              }
            },
            {
              "id": 2,
              "name": "user1",
              "email": "user1@example.com",
              "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
              "isAdmin": false,
              "image": "https://i.imgur.com/aXqPhrK.jpeg",
              "createdAt": "2021-10-19T09:35:54.000Z",
              "updatedAt": "2021-11-25T07:20:28.000Z",
              "Followship": {
                "followerId": 2,
                "followingId": 2,
                "createdAt": "2022-02-14T02:29:24.000Z",
                "updatedAt": "2022-02-14T02:29:24.000Z"
              }
            }
          ],
          "FollowerCount": 2,
          "isFollowed": true
        },
        {
          "id": 41,
          "name": "sss",
          "email": "sss@www.v",
          "password": "$2a$10$n.P5rlX7tHdxbMvoe/Dr.uTRV.tNcYXScKUUOcGd5DmnoDD8JPI4e",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-04T02:57:13.000Z",
          "updatedAt": "2021-11-04T02:57:13.000Z",
          "Followers": [
            {
              "id": 1,
              "name": "root",
              "email": "root@example.com",
              "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
              "isAdmin": false,
              "image": null,
              "createdAt": "2021-10-19T09:35:54.000Z",
              "updatedAt": "2021-10-27T05:23:52.000Z",
              "Followship": {
                "followerId": 1,
                "followingId": 41,
                "createdAt": "2022-02-04T09:41:24.000Z",
                "updatedAt": "2022-02-04T09:41:24.000Z"
              }
            },
            {
              "id": 2,
              "name": "user1",
              "email": "user1@example.com",
              "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
              "isAdmin": false,
              "image": "https://i.imgur.com/aXqPhrK.jpeg",
              "createdAt": "2021-10-19T09:35:54.000Z",
              "updatedAt": "2021-11-25T07:20:28.000Z",
              "Followship": {
                "followerId": 2,
                "followingId": 41,
                "createdAt": "2022-02-14T02:29:31.000Z",
                "updatedAt": "2022-02-14T02:29:31.000Z"
              }
            }
          ],
          "FollowerCount": 2,
          "isFollowed": true
        },
        {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z",
          "Followers": [
            {
              "id": 1,
              "name": "root",
              "email": "root@example.com",
              "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
              "isAdmin": false,
              "image": null,
              "createdAt": "2021-10-19T09:35:54.000Z",
              "updatedAt": "2021-10-27T05:23:52.000Z",
              "Followship": {
                "followerId": 1,
                "followingId": 1,
                "createdAt": "2022-02-15T21:32:40.000Z",
                "updatedAt": "2022-02-15T21:32:40.000Z"
              }
            }
          ],
          "FollowerCount": 1,
          "isFollowed": true
        },
        {
          "id": 61,
          "name": "ts3347@columbia.edu",
          "email": "ts3347@columbia.edu",
          "password": "$2a$10$GDaoDgNXK2W4zJDqZrAC4ekIYNCLnu06JGyqebA59GiXXb./3cm2O",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-26T02:07:29.000Z",
          "updatedAt": "2021-11-26T02:07:29.000Z",
          "Followers": [
            {
              "id": 2,
              "name": "user1",
              "email": "user1@example.com",
              "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
              "isAdmin": false,
              "image": "https://i.imgur.com/aXqPhrK.jpeg",
              "createdAt": "2021-10-19T09:35:54.000Z",
              "updatedAt": "2021-11-25T07:20:28.000Z",
              "Followship": {
                "followerId": 2,
                "followingId": 61,
                "createdAt": "2022-02-09T07:45:06.000Z",
                "updatedAt": "2022-02-09T07:45:06.000Z"
              }
            }
          ],
          "FollowerCount": 1,
          "isFollowed": false
        },
        {
          "id": 81,
          "name": "123",
          "email": "123@gmail.com",
          "password": "$2a$10$nb.j.HLmd7hfufmLbY2jvubI.CjbDFLoHBHACGrIVTlRISSWk9S2a",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-30T15:25:04.000Z",
          "updatedAt": "2021-11-30T15:25:04.000Z",
          "Followers": [
            {
              "id": 2,
              "name": "user1",
              "email": "user1@example.com",
              "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
              "isAdmin": false,
              "image": "https://i.imgur.com/aXqPhrK.jpeg",
              "createdAt": "2021-10-19T09:35:54.000Z",
              "updatedAt": "2021-11-25T07:20:28.000Z",
              "Followship": {
                "followerId": 2,
                "followingId": 81,
                "createdAt": "2021-12-11T07:29:00.000Z",
                "updatedAt": "2021-12-11T07:29:00.000Z"
              }
            }
          ],
          "FollowerCount": 1,
          "isFollowed": false
        },
        {
          "id": 3,
          "name": "user2",
          "email": "user2@example.com",
          "password": "$2a$10$RDuM0nSTb8e5OJergUBAeOecTeGBe.Sr8xWreYzsJsONzZzOvwkDq",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-19T09:35:54.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 11,
          "name": "hello",
          "email": "hello@world.com",
          "password": "$2a$10$NkNjEPVzlLY9FoAqXWHX4.VUZ4baBILjQeZNHxRwCjGf.S7x53Jk6",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-24T12:05:35.000Z",
          "updatedAt": "2021-10-24T12:05:35.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 21,
          "name": "123123",
          "email": "lllxz@outlook.com",
          "password": "$2a$10$tpRNfK/rKPZLM514hUUjKOznSa48cKzF5KlAdEINlRQtAEzXHFOZC",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-02T12:20:39.000Z",
          "updatedAt": "2021-11-02T12:20:39.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 31,
          "name": "Aaaa",
          "email": "aaa@aaa.com",
          "password": "$2a$10$TTBWrEWYfkYw3PXfAyJPy.MwScb7qXwfwvnBk4ZmxkNMWGiaqJaM6",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-02T17:45:46.000Z",
          "updatedAt": "2021-11-02T17:45:46.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 51,
          "name": "asdf",
          "email": "asdf",
          "password": "$2a$10$I.I2uCxwQGea6O6uIDQNjOD5s7QsKHWANsKhYIG18N02eEFnJ86nu",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-16T16:09:50.000Z",
          "updatedAt": "2021-11-16T16:09:50.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 71,
          "name": "dd",
          "email": "dd@ddd.dd",
          "password": "$2a$10$o1Y0HeGkjAKgxh2RwRCKoObBuZRnaGWKnVC0c/zoxCXiFvwa7EMXy",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-30T15:24:40.000Z",
          "updatedAt": "2021-11-30T15:24:40.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 91,
          "name": "test",
          "email": "test@gmail.com",
          "password": "$2a$10$sTG4IvOA4cpc2t8EQutBfOVR6lfo1cmCcAJOgP4RsXjf8H2YXcXBe",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-12-10T03:57:26.000Z",
          "updatedAt": "2021-12-10T03:57:26.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 101,
          "name": "123",
          "email": "123@example.com",
          "password": "$2a$10$av0zzXj62MEtOS0gvH87JuySQPuEuJR6W..5R3s0fuDMnsRmvlntK",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-12-20T14:44:00.000Z",
          "updatedAt": "2021-12-20T14:44:00.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 111,
          "name": "12345",
          "email": "12345@example.com",
          "password": "$2a$10$uNu8OeuyDQ8FPS1NnUXxbu7rkbiykxnYnXH.fEz2KjLBg4k0p/UZu",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-12-20T15:08:40.000Z",
          "updatedAt": "2021-12-20T15:08:40.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 121,
          "name": "123",
          "email": "globelex65@gmail.com",
          "password": "$2a$10$59/zLt8/Qtab/d13Qazi0eZ4NomTyuk/t7qn/kpkJ2p90V5wnQdEu",
          "isAdmin": false,
          "image": "https://i.imgur.com/ZyhIJNv.jpeg",
          "createdAt": "2022-01-04T14:06:53.000Z",
          "updatedAt": "2022-01-04T14:08:17.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 131,
          "name": "aaa",
          "email": "aaa@example.com",
          "password": "$2a$10$wHDZ5mExY0A3rtxkl1CkR.w2vbROwuNzs.sl0udKfbDHyHqWFc.oa",
          "isAdmin": false,
          "image": null,
          "createdAt": "2022-01-04T17:06:05.000Z",
          "updatedAt": "2022-01-04T17:06:05.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 141,
          "name": "张由甲",
          "email": "1127671784@qq.com",
          "password": "$2a$10$Et1zfjVstTxepbWnCcxnLuLvTI8LwU6Lfm6nFzbqlpOmtsZ4L0kUi",
          "isAdmin": false,
          "image": null,
          "createdAt": "2022-01-16T06:03:13.000Z",
          "updatedAt": "2022-01-16T06:03:13.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 151,
          "name": "1234",
          "email": "123@123.123",
          "password": "$2a$10$XO3S8rvwPpScXGuneYMlvOJFADvw1fJMflN5frE3zuaHBrM7GmcF6",
          "isAdmin": false,
          "image": "https://i.imgur.com/40wLHVD.png",
          "createdAt": "2022-01-19T13:49:51.000Z",
          "updatedAt": "2022-01-19T13:50:35.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        },
        {
          "id": 161,
          "name": "👍👍👍",
          "email": "t@2777.dddd",
          "password": "$2a$10$Bt5kuaBIERAq0us74fxh0OzyEJSAet0DeU1jglRrWAf9/f.//Zk86",
          "isAdmin": false,
          "image": null,
          "createdAt": "2022-01-27T12:35:37.000Z",
          "updatedAt": "2022-01-27T12:35:37.000Z",
          "Followers": [],
          "FollowerCount": 0,
          "isFollowed": false
        }
      ]
    }


export default {
  mixins: [emptyImageFilter],
  components: {
    NavTabs,
  },
  data() {
    return {
      users: [],
    }
  },
  created() {
    this.fetchTopUsers()
  },
  methods: {
    fetchTopUsers() {
      this.users = dummyData.users
    },
    addFollowing(userId) {
      this.users = this.users.map((user) => {
        if (user.id === userId) {
          user.isFollowed = true
        }
      })
    },
    deleteFollowing(userId) {
      this.users = this.users.map((user) => {
        if (user.id === userId) {
          user.isFollowed = false
        }
      })
    }
  }
}
</script>
