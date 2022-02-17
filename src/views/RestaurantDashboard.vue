<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>

    <hr>

    <ul>
      <li>評論數： {{ restaurant.commentsLength }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button
        type="button"
        class="btn btn-link"
        @click="$router.back()"
    >
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  "restaurant": {
    "id": 1,
    "name": "Myrtice Rempel",
    "tel": "1-236-483-5268 x15726",
    "address": "73826 Witting Hollow",
    "opening_hours": "08:00",
    "description": "Enim velit dolores in.",
    "image": "https://loremflickr.com/320/240/restaurant,food/?random=34.28664124510033",
    "viewCounts": 214,
    "createdAt": "2021-10-19T09:35:54.000Z",
    "updatedAt": "2022-02-16T16:01:04.000Z",
    "CategoryId": 1,
    "Category": {
      "id": 1,
      "name": "中式料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    },
    "Comments": [
      {
        "id": 1,
        "text": "Voluptatem cupiditate officia ipsam aut architecto omnis perspiciatis expedita explicabo.",
        "UserId": 3,
        "RestaurantId": 1,
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z",
        "User": {
          "id": 3,
          "name": "user2",
          "email": "user2@example.com",
          "password": "$2a$10$RDuM0nSTb8e5OJergUBAeOecTeGBe.Sr8xWreYzsJsONzZzOvwkDq",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-19T09:35:54.000Z"
        }
      },
      {
        "id": 101,
        "text": "Sed nihil esse assumenda aperiam exercitationem.",
        "UserId": 3,
        "RestaurantId": 1,
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z",
        "User": {
          "id": 3,
          "name": "user2",
          "email": "user2@example.com",
          "password": "$2a$10$RDuM0nSTb8e5OJergUBAeOecTeGBe.Sr8xWreYzsJsONzZzOvwkDq",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-19T09:35:54.000Z"
        }
      },
      {
        "id": 251,
        "text": "asd",
        "UserId": 2,
        "RestaurantId": 1,
        "createdAt": "2021-11-13T11:53:25.000Z",
        "updatedAt": "2021-11-13T11:53:25.000Z",
        "User": {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z"
        }
      },
      {
        "id": 261,
        "text": "123",
        "UserId": 1,
        "RestaurantId": 1,
        "createdAt": "2021-11-13T13:57:58.000Z",
        "updatedAt": "2021-11-13T13:57:58.000Z",
        "User": {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z"
        }
      },
      {
        "id": 291,
        "text": "ssss",
        "UserId": 1,
        "RestaurantId": 1,
        "createdAt": "2021-12-02T08:28:17.000Z",
        "updatedAt": "2021-12-02T08:28:17.000Z",
        "User": {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z"
        }
      },
      {
        "id": 301,
        "text": "good",
        "UserId": 1,
        "RestaurantId": 1,
        "createdAt": "2021-12-07T14:58:20.000Z",
        "updatedAt": "2021-12-07T14:58:20.000Z",
        "User": {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z"
        }
      },
      {
        "id": 341,
        "text": null,
        "UserId": 2,
        "RestaurantId": 1,
        "createdAt": "2021-12-20T16:49:17.000Z",
        "updatedAt": "2021-12-20T16:49:17.000Z",
        "User": {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z"
        }
      },
      {
        "id": 371,
        "text": "nice",
        "UserId": 2,
        "RestaurantId": 1,
        "createdAt": "2022-01-08T10:13:17.000Z",
        "updatedAt": "2022-01-08T10:13:17.000Z",
        "User": {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z"
        }
      },
      {
        "id": 381,
        "text": "123",
        "UserId": 1,
        "RestaurantId": 1,
        "createdAt": "2022-01-08T14:58:07.000Z",
        "updatedAt": "2022-01-08T14:58:07.000Z",
        "User": {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z"
        }
      },
      {
        "id": 421,
        "text": "123",
        "UserId": 1,
        "RestaurantId": 1,
        "createdAt": "2022-02-11T02:09:45.000Z",
        "updatedAt": "2022-02-11T02:09:45.000Z",
        "User": {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z"
        }
      }
    ]
  }
}

export default {
  name: 'RestaurantDashboard',
  created() {
    this.fetchRestaurant()
  },
  data() {
    return {
      restaurant: []
    }
  },
  methods: {
    fetchRestaurant() {
      const {id, name, Category, Comments, viewCounts} = dummyData.restaurant
      this.restaurant = {
        ...dummyData.restaurant,
        id,
        name,
        categoryName: Category ? Category.name : '未分類',
        commentsLength: Comments.length,
        viewCounts
      }
      this.isLoading = false
    }
  }
}
</script>