<template>
  <div class="container py-5">
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />

    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard />
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <!-- 分頁標籤 RestaurantPagination -->
    <RestaurantsPagination
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs";
import RestaurantCard from "../components/RestaurantCard";
import RestaurantsNavPills from "../components/RestaurantsNavPills";
import RestaurantsPagination from "../components/RestaurantsPagination";

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Maxie Trantow V",
      tel: "890-533-5519 x71749",
      address: "1268 Bosco Prairie",
      opening_hours: "08:00",
      description: "Officiis aut excepturi ipsa. Et ratione eveniet un",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=51.756313654300044",
      viewCounts: 163,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-03T15:44:06.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 2,
      name: "Ardella Batz",
      tel: "793.250.7899 x5826",
      address: "814 Lubowitz Turnpike",
      opening_hours: "08:00",
      description: "Ipsum sint in impedit. Occaecati ipsum ut. Necessi",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=74.39642698470448",
      viewCounts: 24,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T08:22:21.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 3,
      name: "Harold Hauck",
      tel: "(064) 036-6228 x6320",
      address: "024 Yost Inlet",
      opening_hours: "08:00",
      description: "Delectus iusto facilis. Temporibus blanditiis quid",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=8.88156169757055",
      viewCounts: 15,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T15:30:40.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-29T19:05:15.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 4,
      name: "Gerry Ebert DVM",
      tel: "171-491-6764 x9283",
      address: "81624 McGlynn Skyway",
      opening_hours: "08:00",
      description: "Non quia voluptas eum vero in illum ea asperiores ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=57.05367081822943",
      viewCounts: 4,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-03T15:45:12.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-29T19:05:16.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 5,
      name: "Cyrus Aufderhar",
      tel: "044-687-1298 x361",
      address: "62946 Kristofer Tunnel",
      opening_hours: "08:00",
      description: "Occaecati voluptas odio perspiciatis delectus pari",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=96.10569340226543",
      viewCounts: 3,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-01T09:05:49.000Z",
      CategoryId: 2492,
      Category: null,
      isFavorited: false,
      isLiked: true
    },
    {
      id: 6,
      name: "Dejuan Lemke",
      tel: "1-878-150-9084 x300",
      address: "399 Lueilwitz Islands",
      opening_hours: "08:00",
      description: "Deleniti dolorem aut perferendis id sint voluptate",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=42.92691470956817",
      viewCounts: 3,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T07:13:47.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 7,
      name: "Loyce King",
      tel: "(243) 305-5940",
      address: "76836 Aufderhar Mission",
      opening_hours: "08:00",
      description: "Rerum qui ea.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=17.46646129183562",
      viewCounts: 2,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T06:47:44.000Z",
      CategoryId: 2492,
      Category: null,
      isFavorited: false,
      isLiked: true
    },
    {
      id: 8,
      name: "Dr. Isabella Mann",
      tel: "423-810-1915 x065",
      address: "619 Gislason Radial",
      opening_hours: "08:00",
      description: "Aut occaecati assumenda voluptas eius est saepe se",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=46.54040641576476",
      viewCounts: 3,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T07:13:53.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 9,
      name: "Lindsay Stoltenberg",
      tel: "1-413-683-7333",
      address: "793 Valentine Walks",
      opening_hours: "08:00",
      description: "laudantium",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=9.825477787450376",
      viewCounts: 1,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-30T06:34:52.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      },
      isFavorited: false,
      isLiked: true
    },
    {
      id: 10,
      name: "Kip Heathcote",
      tel: "(234) 261-0553 x328",
      address: "3951 Demarco Burg",
      opening_hours: "08:00",
      description: "repudiandae molestiae eius",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=90.3851170471334",
      viewCounts: 3,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-30T06:46:24.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-29T19:05:16.000Z"
      },
      isFavorited: false,
      isLiked: false
    }
  ],
  categories: [
    {
      id: 2,
      name: "日本料理",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-29T19:05:15.000Z"
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-29T19:05:16.000Z"
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-23T10:08:45.000Z"
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-23T10:08:45.000Z"
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-23T10:08:45.000Z"
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-23T10:08:45.000Z"
    },
    {
      id: 2522,
      name: "好好吃料理",
      createdAt: "2020-12-01T15:10:10.000Z",
      updatedAt: "2020-12-03T06:43:17.000Z"
    }
  ],
  categoryId: "",
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2
};

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next
      } = dummyData;
      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = page;
      this.totalPage = totalPage;
      this.previousPage = prev;
      this.nextPage = next;
    }
  }
};
</script>