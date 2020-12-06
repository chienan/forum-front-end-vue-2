<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">最新動態</h1>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <NewestRestaurants :restaurants="restaurants" />
        <!-- 最新餐廳 NewestRestaurants -->
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments :comments="comments" />
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs";
import NewestRestaurants from "../components/NewestRestaurants";
import NewestComments from "../components/NewestComments";

const dummyData = {
  restaurants: [
    {
      id: 2602,
      name: "123",
      tel: "123",
      address: "台北市",
      opening_hours: "15:33",
      description: "123",
      image: "https://i.imgur.com/nxyDBNH.jpeg",
      viewCounts: 1,
      createdAt: "2020-12-01T07:31:08.000Z",
      updatedAt: "2020-12-02T07:20:40.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      }
    },
    {
      id: 1,
      name: "Maxie Trantow V",
      tel: "890-533-5519 x71749",
      address: "1268 Bosco Prairie",
      opening_hours: "08:00",
      description:
        "Officiis aut excepturi ipsa. Et ratione eveniet unde laboriosam aut. Explicabo autem eos pariatur aut molestiae perspiciatis debitis. Et repellat consequatur sapiente velit.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=51.756313654300044",
      viewCounts: 147,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T08:21:35.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      }
    },
    {
      id: 2,
      name: "Ardella Batz",
      tel: "793.250.7899 x5826",
      address: "814 Lubowitz Turnpike",
      opening_hours: "08:00",
      description:
        "Ipsum sint in impedit. Occaecati ipsum ut. Necessitatibus id culpa.\n \rNatus ipsa quis molestiae ab aperiam expedita enim impedit. Eius velit iure fugiat quibusdam. Autem ipsam voluptate voluptatem nihil. Vel ut iure alias. Eius nihil quis doloremque. Sint officia atque sunt amet fuga nihil ducimus.\n \rLabore laborum rerum tempore ratione consequatur dolorem. Veritatis sint nisi dolor hic ut ut aut alias veritatis. Et commodi officiis vero reiciendis provident. Soluta sit doloribus autem qui quo molestias magni unde quibusdam.",
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
      }
    },
    {
      id: 3,
      name: "Harold Hauck",
      tel: "(064) 036-6228 x6320",
      address: "024 Yost Inlet",
      opening_hours: "08:00",
      description:
        "Delectus iusto facilis. Temporibus blanditiis quidem aut odit libero. Pariatur voluptatem iste quo velit doloribus deleniti et. Ad dolor autem ipsum ea nam placeat consectetur quidem. Eius nobis iure ipsum iure.\n \rMinus voluptatum perspiciatis vel esse. Sit qui blanditiis in ab et quod ut suscipit placeat. Minus modi provident sit nisi est repudiandae omnis delectus non. Assumenda soluta sit eum eum. Dolorum quidem et deleniti commodi dolores pariatur. Voluptatem ab aliquam totam minima totam atque.\n \rSed cum dicta magnam reiciendis doloremque occaecati. Fugiat voluptatem perspiciatis dicta id eveniet praesentium autem totam. Omnis omnis illo ratione pariatur neque consequuntur deserunt soluta natus. Voluptatum et labore consectetur voluptatibus nihil et mollitia.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=8.88156169757055",
      viewCounts: 12,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T07:13:38.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-29T19:05:15.000Z"
      }
    },
    {
      id: 4,
      name: "Gerry Ebert DVM",
      tel: "171-491-6764 x9283",
      address: "81624 McGlynn Skyway",
      opening_hours: "08:00",
      description: "Non quia voluptas eum vero in illum ea asperiores et.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=57.05367081822943",
      viewCounts: 2,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-02T07:12:24.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-29T19:05:16.000Z"
      }
    },
    {
      id: 5,
      name: "Cyrus Aufderhar",
      tel: "044-687-1298 x361",
      address: "62946 Kristofer Tunnel",
      opening_hours: "08:00",
      description:
        "Occaecati voluptas odio perspiciatis delectus pariatur quia deserunt. Voluptas vero asperiores non. Consequatur consequatur totam deleniti quia soluta alias. Temporibus minus eos magni. Aut labore dolorem minima suscipit porro quod inventore.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=96.10569340226543",
      viewCounts: 3,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-01T09:05:49.000Z",
      CategoryId: 2492,
      Category: null
    },
    {
      id: 6,
      name: "Dejuan Lemke",
      tel: "1-878-150-9084 x300",
      address: "399 Lueilwitz Islands",
      opening_hours: "08:00",
      description:
        "Deleniti dolorem aut perferendis id sint voluptatem quia consequuntur quisquam. Aspernatur fugiat dolorem et fugit. Qui velit autem unde inventore pariatur quia ipsum adipisci. Fugiat velit assumenda voluptates aliquid aliquam eius. Repellendus sit provident quam eius et quia officiis cum.\n \rMagni eum tempore ea est. Minima quo at. Repellat cumque eligendi hic doloremque illo et reiciendis porro.\n \rPraesentium odit aliquid libero dolore nemo. Et rerum sapiente. Quidem tenetur aut perferendis excepturi quo facere enim. Quia est debitis omnis rerum quia nihil sed maiores consequatur. Impedit ut unde voluptatem ipsam ut occaecati voluptatibus ut.",
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
      }
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
      Category: null
    },
    {
      id: 8,
      name: "Dr. Isabella Mann",
      tel: "423-810-1915 x065",
      address: "619 Gislason Radial",
      opening_hours: "08:00",
      description:
        "Aut occaecati assumenda voluptas eius est saepe sed. Accusantium qui natus vel vel voluptatem distinctio est sint. Reprehenderit doloribus voluptas doloremque architecto quis harum facilis aut. Hic placeat tempora et qui id. Velit hic qui numquam nihil voluptatem consectetur nesciunt rerum est.",
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
      }
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
      }
    }
  ],
  comments: [
    {
      id: 5962,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:55:38.000Z",
      updatedAt: "2020-12-02T07:55:38.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5942,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:55:17.000Z",
      updatedAt: "2020-12-02T07:55:17.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5922,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:54:06.000Z",
      updatedAt: "2020-12-02T07:54:06.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5902,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:53:00.000Z",
      updatedAt: "2020-12-02T07:53:00.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5882,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:52:39.000Z",
      updatedAt: "2020-12-02T07:52:39.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5862,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:51:56.000Z",
      updatedAt: "2020-12-02T07:51:56.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5842,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:51:19.000Z",
      updatedAt: "2020-12-02T07:51:19.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5822,
      text: null,
      UserId: 932,
      RestaurantId: null,
      createdAt: "2020-12-02T07:46:40.000Z",
      updatedAt: "2020-12-02T07:46:40.000Z",
      User: {
        id: 932,
        name: "王曉明",
        email: "123456@gmail.com",
        password:
          "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
        isAdmin: false,
        image: null,
        createdAt: "2020-12-01T09:20:12.000Z",
        updatedAt: "2020-12-01T09:20:12.000Z"
      },
      Restaurant: null
    },
    {
      id: 5812,
      text: null,
      UserId: 1,
      RestaurantId: null,
      createdAt: "2020-12-02T07:46:10.000Z",
      updatedAt: "2020-12-02T07:46:10.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$0dBI.8S//NhlGeouBUbV3.oBDkdbbqXObuMJyuS.PHxjzdW/PvqYy",
        isAdmin: true,
        image: null,
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      },
      Restaurant: null
    },
    {
      id: 5772,
      text: "HAHAHAHAHA",
      UserId: 1,
      RestaurantId: 1,
      createdAt: "2020-11-30T07:34:04.000Z",
      updatedAt: "2020-11-30T07:34:04.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$0dBI.8S//NhlGeouBUbV3.oBDkdbbqXObuMJyuS.PHxjzdW/PvqYy",
        isAdmin: true,
        image: null,
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-11-23T10:08:45.000Z"
      },
      Restaurant: {
        id: 1,
        name: "Maxie Trantow V",
        tel: "890-533-5519 x71749",
        address: "1268 Bosco Prairie",
        opening_hours: "08:00",
        description:
          "Officiis aut excepturi ipsa. Et ratione eveniet unde laboriosam aut. Explicabo autem eos pariatur aut molestiae perspiciatis debitis. Et repellat consequatur sapiente velit.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=51.756313654300044",
        viewCounts: 147,
        createdAt: "2020-11-23T10:08:45.000Z",
        updatedAt: "2020-12-02T08:21:35.000Z",
        CategoryId: 4
      }
    }
  ]
};

export default {
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments
  },
  data() {
    return {
      restaurants: [],
      comments: []
    };
  },
  created() {
    this.fetchFeeds();
  },
  methods: {
    fetchFeeds() {
      const { restaurants, comments } = dummyData;
      this.restaurants = restaurants;
      this.comments = comments.filter(
        comment => comment.Restaurant && comment.text
      );
    }
  }
};
</script>