// ./src/components/AdminRestaurantsTable.vue
<template>
  <table class="table">
    <thead class="thead-dark">
    <tr>
      <th scope="col">
        #
      </th>
      <th scope="col">
        Category
      </th>
      <th scope="col">
        Name
      </th>
      <th
          scope="col"
          width="300"
      >
        操作
      </th>
    </tr>
    </thead>
    <tbody>
    <tr
        v-for="restaurant in restaurants"
        :key="restaurant.id"
    >
      <th scope="row">
        {{ restaurant.id }}
      </th>
      <td>{{ restaurant.Category ? restaurant.Category.name : '未分類' }}</td>
      <td>{{ restaurant.name }}</td>
      <td class="d-flex justify-content-between">
        <router-link :to="{name: 'admin-restaurant', params: {id: restaurant.id}}" class="btn btn-link">
          Show
        </router-link>

        <a
            href="#"
            class="btn btn-link"
        >Edit</a>

        <button
            type="button"
            class="btn btn-link"
            @click.stop.prevent="deleteRestaurant(restaurant.id)"
        >
          Delete
        </button>
      </td>
    </tr>
    </tbody>
  </table>
</template>

<script>
const dummyData = {
  "restaurants": [
    {
      "id": 1,
      "name": "Myrtice Rempel",
      "tel": "1-236-483-5268 x15726",
      "address": "73826 Witting Hollow",
      "opening_hours": "08:00",
      "description": "Enim velit dolores in.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=34.28664124510033",
      "viewCounts": 228,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-03-07T16:01:49.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 2,
      "name": "Dario Dickens Sr.",
      "tel": "1-566-833-7180 x557",
      "address": "123 Nolan Grove",
      "opening_hours": "08:00",
      "description": "Expedita asperiores qui. Possimus rerum amet vel v",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=80.20150144403091",
      "viewCounts": 46,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-03-01T12:57:03.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": true,
      "isLiked": true
    },
    {
      "id": 3,
      "name": "Gladyce Zulauf",
      "tel": "495-012-4903",
      "address": "7827 Hoppe Summit",
      "opening_hours": "08:00",
      "description": "Error dicta est vitae at voluptatem.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=16.04765635982797",
      "viewCounts": 22,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-02-18T02:33:15.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": true,
      "isLiked": false
    },
    {
      "id": 4,
      "name": "Eda Carter",
      "tel": "(067) 802-7379 x47783",
      "address": "21622 Amiya Dale",
      "opening_hours": "08:00",
      "description": "et",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=1.7593104092412881",
      "viewCounts": 1,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-01-31T12:04:06.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": false,
      "isLiked": true
    },
    {
      "id": 5,
      "name": "Alek Labadie",
      "tel": "831-876-5248 x31782",
      "address": "0439 Hammes Unions",
      "opening_hours": "08:00",
      "description": "omnis",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=28.32250437970567",
      "viewCounts": 11,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-02-17T03:38:26.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 6,
      "name": "Santos Hills",
      "tel": "553-191-2308",
      "address": "78746 Weimann Union",
      "opening_hours": "08:00",
      "description": "Delectus et ea exercitationem recusandae delectus ",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.36316738677164",
      "viewCounts": 3,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-12-02T01:45:59.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 7,
      "name": "Mrs. Terrance Goldner",
      "tel": "(273) 548-0319",
      "address": "295 Gutmann Cove",
      "opening_hours": "08:00",
      "description": "fuga",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=25.279235663053367",
      "viewCounts": 7,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-01-19T02:39:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": false,
      "isLiked": true
    },
    {
      "id": 8,
      "name": "Bradley Hansen",
      "tel": "1-653-737-3374",
      "address": "9311 Rita Locks",
      "opening_hours": "08:00",
      "description": "Qui aliquid itaque itaque et ut recusandae velit q",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=42.66778164759013",
      "viewCounts": 40,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-02-18T09:14:07.000Z",
      "CategoryId": 4,
      "Category": {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 9,
      "name": "Ezra Metz",
      "tel": "982.086.6236 x3942",
      "address": "73491 Goodwin Crossroad",
      "opening_hours": "08:00",
      "description": "Voluptas hic at rem. Similique occaecati libero re",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=47.59333981051594",
      "viewCounts": 5,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-01-21T04:52:17.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": true,
      "isLiked": false
    },
    {
      "id": 10,
      "name": "Logan Wolf V",
      "tel": "(129) 312-1031 x3330",
      "address": "010 Littel Track",
      "opening_hours": "08:00",
      "description": "rerum enim rerum",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=21.281958268620492",
      "viewCounts": 16,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-01-17T09:25:57.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2021-10-19T09:35:54.000Z",
        "updatedAt": "2021-10-19T09:35:54.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    }
  ],
  "categories": [
    {
      "id": 1,
      "name": "中式料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    },
    {
      "id": 2,
      "name": "日本料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    },
    {
      "id": 3,
      "name": "義大利料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    },
    {
      "id": 4,
      "name": "墨西哥料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    },
    {
      "id": 5,
      "name": "素食料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    },
    {
      "id": 6,
      "name": "美式料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    },
    {
      "id": 7,
      "name": "複合式料理",
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z"
    }
  ],
  "categoryId": "",
  "page": 1,
  "totalPage": [
    1,
    2,
    3,
    4,
    5
  ],
  "prev": 1,
  "next": 2
}

export default {
  data() {
    return {
      restaurants: []
    }
  },
  created() {
    this.fetchRestaurants()
  },
  methods: {
    fetchRestaurants() {
      this.restaurants = dummyData.restaurants
    },
    deleteRestaurant(restaurantId){
      this.restaurants = this.restaurants.filter( restaurant => restaurant.id !== restaurantId)
    }
  }
}
</script>