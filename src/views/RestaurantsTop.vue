<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">
      人氣餐廳
    </h1>

    <hr>
    <div
        class="card mb-3"
        style="max-width: 540px;margin: auto;"
        v-for="restaurant in restaurants"
        :key="restaurant.id"
    >
      <div class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img
                class="card-img"
                :src="restaurant.image |emptyImage"
            >
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">
              {{restaurant.name}}
            </h5>
            <span class="badge badge-secondary">收藏數：{{restaurant.FavoriteCount}}</span>
            <p class="card-text">
              {{restaurant.description}}
            </p>
            <a
                href="#"
                class="btn btn-primary mr-2"
            >Show</a>

            <button
                v-if="restaurant.isFavorited"
                type="button"
                class="btn btn-danger mr-2"
            >
              移除最愛
            </button>
            <button
                v-else
                type="button"
                class="btn btn-primary"
            >
              加到最愛
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from './../components/NavTabs'
import {emptyImageFilter} from './../utils/mixins'

const dummyData = {
  "restaurants": [
    {
      "id": 2,
      "name": "Dario Dickens Sr.",
      "tel": "1-566-833-7180 x557",
      "address": "123 Nolan Grove",
      "opening_hours": "08:00",
      "description": "Expedita asperiores qui. Possimus rerum amet vel v",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=80.20150144403091",
      "viewCounts": 43,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-02-10T13:57:15.000Z",
      "CategoryId": 1,
      "FavoritedUsers": [
        {
          "id": 3,
          "name": "user2",
          "email": "user2@example.com",
          "password": "$2a$10$RDuM0nSTb8e5OJergUBAeOecTeGBe.Sr8xWreYzsJsONzZzOvwkDq",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-19T09:35:54.000Z",
          "Favorite": {
            "UserId": 3,
            "RestaurantId": 2,
            "createdAt": "2022-01-10T05:08:01.000Z",
            "updatedAt": "2022-01-10T05:08:01.000Z"
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
          "Favorite": {
            "UserId": 2,
            "RestaurantId": 2,
            "createdAt": "2022-01-17T06:00:28.000Z",
            "updatedAt": "2022-01-17T06:00:28.000Z"
          }
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
          "Favorite": {
            "UserId": 151,
            "RestaurantId": 2,
            "createdAt": "2022-01-28T03:05:54.000Z",
            "updatedAt": "2022-01-28T03:05:54.000Z"
          }
        }
      ],
      "isFavorited": false,
      "FavoriteCount": 3
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
      "FavoritedUsers": [
        {
          "id": 81,
          "name": "123",
          "email": "123@gmail.com",
          "password": "$2a$10$nb.j.HLmd7hfufmLbY2jvubI.CjbDFLoHBHACGrIVTlRISSWk9S2a",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-30T15:25:04.000Z",
          "updatedAt": "2021-11-30T15:25:04.000Z",
          "Favorite": {
            "UserId": 81,
            "RestaurantId": 10,
            "createdAt": "2021-11-30T15:26:16.000Z",
            "updatedAt": "2021-11-30T15:26:16.000Z"
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
          "Favorite": {
            "UserId": 2,
            "RestaurantId": 10,
            "createdAt": "2022-01-10T07:50:06.000Z",
            "updatedAt": "2022-01-10T07:50:06.000Z"
          }
        }
      ],
      "isFavorited": false,
      "FavoriteCount": 2
    },
    {
      "id": 8,
      "name": "Bradley Hansen",
      "tel": "1-653-737-3374",
      "address": "9311 Rita Locks",
      "opening_hours": "08:00",
      "description": "Qui aliquid itaque itaque et ut recusandae velit q",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=42.66778164759013",
      "viewCounts": 37,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-02-16T15:06:02.000Z",
      "CategoryId": 4,
      "FavoritedUsers": [
        {
          "id": 21,
          "name": "123123",
          "email": "lllxz@outlook.com",
          "password": "$2a$10$tpRNfK/rKPZLM514hUUjKOznSa48cKzF5KlAdEINlRQtAEzXHFOZC",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-11-02T12:20:39.000Z",
          "updatedAt": "2021-11-02T12:20:39.000Z",
          "Favorite": {
            "UserId": 21,
            "RestaurantId": 8,
            "createdAt": "2021-11-02T12:22:04.000Z",
            "updatedAt": "2021-11-02T12:22:04.000Z"
          }
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
          "Favorite": {
            "UserId": 3,
            "RestaurantId": 8,
            "createdAt": "2022-01-10T05:08:05.000Z",
            "updatedAt": "2022-01-10T05:08:05.000Z"
          }
        }
      ],
      "isFavorited": false,
      "FavoriteCount": 2
    },
    {
      "id": 3,
      "name": "Gladyce Zulauf",
      "tel": "495-012-4903",
      "address": "7827 Hoppe Summit",
      "opening_hours": "08:00",
      "description": "Error dicta est vitae at voluptatem.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=16.04765635982797",
      "viewCounts": 21,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-02-11T02:05:54.000Z",
      "CategoryId": 3,
      "FavoritedUsers": [
        {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z",
          "Favorite": {
            "UserId": 2,
            "RestaurantId": 3,
            "createdAt": "2021-12-14T05:36:09.000Z",
            "updatedAt": "2021-12-14T05:36:09.000Z"
          }
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
          "Favorite": {
            "UserId": 1,
            "RestaurantId": 3,
            "createdAt": "2022-01-06T05:52:09.000Z",
            "updatedAt": "2022-01-06T05:52:09.000Z"
          }
        }
      ],
      "isFavorited": true,
      "FavoriteCount": 2
    },
    {
      "id": 50,
      "name": "Hadley Adams",
      "tel": "820.488.7695",
      "address": "497 Raymond Mews",
      "opening_hours": "08:00",
      "description": "Cum ex aut ducimus eos architecto. Est voluptatem ",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=39.917667503022834",
      "viewCounts": 2,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-12-07T07:48:33.000Z",
      "CategoryId": 2,
      "FavoritedUsers": [
        {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z",
          "Favorite": {
            "UserId": 1,
            "RestaurantId": 50,
            "createdAt": "2022-02-15T04:58:26.000Z",
            "updatedAt": "2022-02-15T04:58:26.000Z"
          }
        }
      ],
      "isFavorited": true,
      "FavoriteCount": 1
    },
    {
      "id": 43,
      "name": "Jamil Hackett",
      "tel": "(292) 319-8896",
      "address": "740 Soledad Landing",
      "opening_hours": "08:00",
      "description": "Dolore numquam odio sunt enim animi velit et offic",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=2.9322478840739574",
      "viewCounts": 4,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-02-08T11:50:06.000Z",
      "CategoryId": 5,
      "FavoritedUsers": [
        {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z",
          "Favorite": {
            "UserId": 2,
            "RestaurantId": 43,
            "createdAt": "2022-02-08T11:50:04.000Z",
            "updatedAt": "2022-02-08T11:50:04.000Z"
          }
        }
      ],
      "isFavorited": false,
      "FavoriteCount": 1
    },
    {
      "id": 33,
      "name": "Dr. Bella Hodkiewicz",
      "tel": "(689) 612-8769 x238",
      "address": "35782 Heaney Path",
      "opening_hours": "08:00",
      "description": "Magni perspiciatis corrupti. Inventore quidem quo ",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=10.754887334888942",
      "viewCounts": 0,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2021-10-19T09:35:54.000Z",
      "CategoryId": 1,
      "FavoritedUsers": [
        {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$hWARc0RhdL/93XckpRCfdOerrvS7Ye.iZ0e0LkYV8PVfZy/xDWRNW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-10-27T05:23:52.000Z",
          "Favorite": {
            "UserId": 1,
            "RestaurantId": 33,
            "createdAt": "2022-01-22T10:21:54.000Z",
            "updatedAt": "2022-01-22T10:21:54.000Z"
          }
        }
      ],
      "isFavorited": true,
      "FavoriteCount": 1
    },
    {
      "id": 25,
      "name": "Anya Kunze",
      "tel": "699.310.4164 x8478",
      "address": "13020 Koelpin Ridge",
      "opening_hours": "08:00",
      "description": "animi hic esse",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=39.59726429643153",
      "viewCounts": 3,
      "createdAt": "2021-10-19T09:35:54.000Z",
      "updatedAt": "2022-01-14T15:55:44.000Z",
      "CategoryId": 2,
      "FavoritedUsers": [
        {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z",
          "Favorite": {
            "UserId": 2,
            "RestaurantId": 25,
            "createdAt": "2022-01-14T15:55:38.000Z",
            "updatedAt": "2022-01-14T15:55:38.000Z"
          }
        }
      ],
      "isFavorited": false,
      "FavoriteCount": 1
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
      "FavoritedUsers": [
        {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z",
          "Favorite": {
            "UserId": 2,
            "RestaurantId": 9,
            "createdAt": "2022-02-08T11:28:21.000Z",
            "updatedAt": "2022-02-08T11:28:21.000Z"
          }
        }
      ],
      "isFavorited": false,
      "FavoriteCount": 1
    },
    {
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
      "FavoritedUsers": [
        {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$Amu86uI4I7RyT/UGdzHISufp/HqN6u6680DeGDNz.q1gpgPxuKW7i",
          "isAdmin": false,
          "image": "https://i.imgur.com/aXqPhrK.jpeg",
          "createdAt": "2021-10-19T09:35:54.000Z",
          "updatedAt": "2021-11-25T07:20:28.000Z",
          "Favorite": {
            "UserId": 2,
            "RestaurantId": 1,
            "createdAt": "2022-02-06T05:46:33.000Z",
            "updatedAt": "2022-02-06T05:46:33.000Z"
          }
        }
      ],
      "isFavorited": false,
      "FavoriteCount": 1
    }
  ]
}
export default{
  mixins:[emptyImageFilter],
  components:{
    NavTabs
  },
  data(){
    return{
      restaurants:this.fetchRestaurant()
    }
  },
  methods:{
    fetchRestaurant(){
      return this.restaurants = dummyData.restaurants
    }
  }
}
</script>