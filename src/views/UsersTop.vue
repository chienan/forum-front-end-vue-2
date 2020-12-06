<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
      <div v-for="user in users" :key="user.id" class="col-3">
        <img :src="user.image" width="140px" height="140px" />
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary">追蹤人數：{{ user.FollowerCount? user.FollowerCount : '0' }}</span>
        <p class="mt-3">
          <button v-if="unfollow" type="button" class="btn btn-danger">取消追蹤</button>
          <button v-else type="button" class="btn btn-primary">追蹤</button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs";

const dummyData = {
  users: [
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$s7ShjXk/VR4nVoFtm9PLG.LR6x7wv77vwouGXoKssT7Xfk/rOsQZe",
      isAdmin: true,
      image: "https://i.imgur.com/Cr9tfAu.jpg",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-03T08:38:38.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$s7ShjXk/VR4nVoFtm9PLG.LR6x7wv77vwouGXoKssT7Xfk/rOsQZe",
          isAdmin: true,
          image: "https://i.imgur.com/Cr9tfAu.jpg",
          createdAt: "2020-11-23T10:08:45.000Z",
          updatedAt: "2020-12-03T08:38:38.000Z",
          Followship: {
            followerId: 2,
            followingId: 2,
            createdAt: "2020-03-25T07:52:27.000Z",
            updatedAt: "2020-03-25T07:52:27.000Z"
          }
        },
        {
          id: 932,
          name: "王曉明",
          email: "123456@gmail.com",
          password:
            "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
          isAdmin: false,
          image: null,
          createdAt: "2020-12-01T09:20:12.000Z",
          updatedAt: "2020-12-03T08:41:27.000Z",
          Followship: {
            followerId: 932,
            followingId: 2,
            createdAt: "2020-12-03T08:43:35.000Z",
            updatedAt: "2020-12-03T08:43:35.000Z"
          }
        },
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$0dBI.8S//NhlGeouBUbV3.oBDkdbbqXObuMJyuS.PHxjzdW/PvqYy",
          isAdmin: true,
          image: null,
          createdAt: "2020-11-23T10:08:45.000Z",
          updatedAt: "2020-11-23T10:08:45.000Z",
          Followship: {
            followerId: 1,
            followingId: 2,
            createdAt: "2020-12-03T14:50:32.000Z",
            updatedAt: "2020-12-03T14:50:32.000Z"
          }
        },
        {
          id: 942,
          name: "happy",
          email: "123@gmail.com",
          password:
            "$2a$10$OZJy/T5fYv.S4SfIeGFIYe8VetSmhtjK07yXAvUzafKUDv1HVe7yq",
          isAdmin: false,
          image: "https://i.imgur.com/NGYrvVa.jpeg",
          createdAt: "2020-12-03T08:45:00.000Z",
          updatedAt: "2020-12-03T08:45:40.000Z",
          Followship: {
            followerId: 942,
            followingId: 2,
            createdAt: "2020-12-03T15:05:37.000Z",
            updatedAt: "2020-12-03T15:05:37.000Z"
          }
        }
      ],
      FollowerCount: 4,
      isFollowed: true
    },
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$0dBI.8S//NhlGeouBUbV3.oBDkdbbqXObuMJyuS.PHxjzdW/PvqYy",
      isAdmin: true,
      image: null,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-23T10:08:45.000Z",
      Followers: [
        {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$0dBI.8S//NhlGeouBUbV3.oBDkdbbqXObuMJyuS.PHxjzdW/PvqYy",
          isAdmin: true,
          image: null,
          createdAt: "2020-11-23T10:08:45.000Z",
          updatedAt: "2020-11-23T10:08:45.000Z",
          Followship: {
            followerId: 1,
            followingId: 1,
            createdAt: "2020-12-03T14:50:30.000Z",
            updatedAt: "2020-12-03T14:50:30.000Z"
          }
        },
        {
          id: 942,
          name: "happy",
          email: "123@gmail.com",
          password:
            "$2a$10$OZJy/T5fYv.S4SfIeGFIYe8VetSmhtjK07yXAvUzafKUDv1HVe7yq",
          isAdmin: false,
          image: "https://i.imgur.com/NGYrvVa.jpeg",
          createdAt: "2020-12-03T08:45:00.000Z",
          updatedAt: "2020-12-03T08:45:40.000Z",
          Followship: {
            followerId: 942,
            followingId: 1,
            createdAt: "2020-12-03T14:57:19.000Z",
            updatedAt: "2020-12-03T14:57:19.000Z"
          }
        }
      ],
      FollowerCount: 2,
      isFollowed: true
    },
    {
      id: 902,
      name: "Serena",
      email: "serena@gmail.com",
      password: "$2a$10$qh4WPjAiZsOxg2sCF2KEP.4P7p9kS6vAeTujIr3cZXfE3vaWVqUMO",
      isAdmin: false,
      image: null,
      createdAt: "2020-11-23T10:13:44.000Z",
      updatedAt: "2020-11-23T10:13:44.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$s7ShjXk/VR4nVoFtm9PLG.LR6x7wv77vwouGXoKssT7Xfk/rOsQZe",
          isAdmin: true,
          image: "https://i.imgur.com/Cr9tfAu.jpg",
          createdAt: "2020-11-23T10:08:45.000Z",
          updatedAt: "2020-12-03T08:38:38.000Z",
          Followship: {
            followerId: 2,
            followingId: 902,
            createdAt: "2020-11-30T05:36:48.000Z",
            updatedAt: "2020-11-30T05:36:48.000Z"
          }
        },
        {
          id: 942,
          name: "happy",
          email: "123@gmail.com",
          password:
            "$2a$10$OZJy/T5fYv.S4SfIeGFIYe8VetSmhtjK07yXAvUzafKUDv1HVe7yq",
          isAdmin: false,
          image: "https://i.imgur.com/NGYrvVa.jpeg",
          createdAt: "2020-12-03T08:45:00.000Z",
          updatedAt: "2020-12-03T08:45:40.000Z",
          Followship: {
            followerId: 942,
            followingId: 902,
            createdAt: "2020-12-03T15:14:09.000Z",
            updatedAt: "2020-12-03T15:14:09.000Z"
          }
        }
      ],
      FollowerCount: 2,
      isFollowed: false
    },
    {
      id: 912,
      name: "123",
      email: "123@123",
      password: "$2a$10$eHSHhg/V3oNLm59hWWVDyeE3JA6Ufyq7ztCvsqkMaUxk382df4Oq6",
      isAdmin: false,
      image: null,
      createdAt: "2020-11-29T17:19:13.000Z",
      updatedAt: "2020-11-29T17:19:13.000Z",
      Followers: [
        {
          id: 932,
          name: "王曉明",
          email: "123456@gmail.com",
          password:
            "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
          isAdmin: false,
          image: null,
          createdAt: "2020-12-01T09:20:12.000Z",
          updatedAt: "2020-12-03T08:41:27.000Z",
          Followship: {
            followerId: 932,
            followingId: 912,
            createdAt: "2020-12-03T08:44:10.000Z",
            updatedAt: "2020-12-03T08:44:10.000Z"
          }
        },
        {
          id: 942,
          name: "happy",
          email: "123@gmail.com",
          password:
            "$2a$10$OZJy/T5fYv.S4SfIeGFIYe8VetSmhtjK07yXAvUzafKUDv1HVe7yq",
          isAdmin: false,
          image: "https://i.imgur.com/NGYrvVa.jpeg",
          createdAt: "2020-12-03T08:45:00.000Z",
          updatedAt: "2020-12-03T08:45:40.000Z",
          Followship: {
            followerId: 942,
            followingId: 912,
            createdAt: "2020-12-03T15:14:17.000Z",
            updatedAt: "2020-12-03T15:14:17.000Z"
          }
        }
      ],
      FollowerCount: 2,
      isFollowed: false
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$TPKFC8BS5/E37CFM3kx8yOPya6L5ifI0S8aFQ7b3jdA.oEzjXwYby",
      isAdmin: false,
      image: null,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-11-23T10:08:45.000Z",
      Followers: [
        {
          id: 942,
          name: "happy",
          email: "123@gmail.com",
          password:
            "$2a$10$OZJy/T5fYv.S4SfIeGFIYe8VetSmhtjK07yXAvUzafKUDv1HVe7yq",
          isAdmin: false,
          image: "https://i.imgur.com/NGYrvVa.jpeg",
          createdAt: "2020-12-03T08:45:00.000Z",
          updatedAt: "2020-12-03T08:45:40.000Z",
          Followship: {
            followerId: 942,
            followingId: 3,
            createdAt: "2020-12-03T14:57:23.000Z",
            updatedAt: "2020-12-03T14:57:23.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 942,
      name: "happy",
      email: "123@gmail.com",
      password: "$2a$10$OZJy/T5fYv.S4SfIeGFIYe8VetSmhtjK07yXAvUzafKUDv1HVe7yq",
      isAdmin: false,
      image: "https://i.imgur.com/NGYrvVa.jpeg",
      createdAt: "2020-12-03T08:45:00.000Z",
      updatedAt: "2020-12-03T08:45:40.000Z",
      Followers: [
        {
          id: 932,
          name: "王曉明",
          email: "123456@gmail.com",
          password:
            "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
          isAdmin: false,
          image: null,
          createdAt: "2020-12-01T09:20:12.000Z",
          updatedAt: "2020-12-03T08:41:27.000Z",
          Followship: {
            followerId: 932,
            followingId: 942,
            createdAt: "2020-12-03T08:55:32.000Z",
            updatedAt: "2020-12-03T08:55:32.000Z"
          }
        }
      ],
      FollowerCount: 1,
      isFollowed: false
    },
    {
      id: 922,
      name: "111",
      email: "111@111",
      password: "$2a$10$Tm5YIdzQb7recZgv/A5ltuS.UtwwyovNqWYr45QfFpBk/vtU3Ppce",
      isAdmin: false,
      image: null,
      createdAt: "2020-11-29T17:42:08.000Z",
      updatedAt: "2020-11-29T17:42:08.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    },
    {
      id: 932,
      name: "王曉明",
      email: "123456@gmail.com",
      password: "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-01T09:20:12.000Z",
      updatedAt: "2020-12-03T08:41:27.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false
    }
  ]
};

export default {
  components: {
    NavTabs
  },
  data() {
    return {
      users: []
    };
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    fetchUsers() {
      this.users = dummyData.users;
    }
  }
};
</script>