<template>
  <div class="container py-5">
    <!-- AdminNav Component -->

    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Email</th>
          <th scope="col">Role</th>
          <th scope="col" width="140">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <th scope="row">{{user.id}}</th>
          <td>{{user.email}}</td>
          <td>{{user.isAdmin ? 'admin' : 'users'}}</td>
          <td>
            <button
              v-if="currentUser.id !== user.id"
              type="button"
              class="btn btn-link"
              @click="toggleUserRole(user)"
            >{{user.isAdmin ? 'set as user' : 'set as admin'}}</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
const dummyData = {
  users: [
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$0dBI.8S//NhlGeouBUbV3.oBDkdbbqXObuMJyuS.PHxjzdW/PvqYy",
      isAdmin: true,
      image: null,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-04T20:56:30.000Z"
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$s7ShjXk/VR4nVoFtm9PLG.LR6x7wv77vwouGXoKssT7Xfk/rOsQZe",
      isAdmin: true,
      image: "https://i.imgur.com/zFLL9vN.png",
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-07T09:31:21.000Z"
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$TPKFC8BS5/E37CFM3kx8yOPya6L5ifI0S8aFQ7b3jdA.oEzjXwYby",
      isAdmin: true,
      image: null,
      createdAt: "2020-11-23T10:08:45.000Z",
      updatedAt: "2020-12-07T09:31:22.000Z"
    },
    {
      id: 902,
      name: "Serena",
      email: "serena@gmail.com",
      password: "$2a$10$qh4WPjAiZsOxg2sCF2KEP.4P7p9kS6vAeTujIr3cZXfE3vaWVqUMO",
      isAdmin: true,
      image: null,
      createdAt: "2020-11-23T10:13:44.000Z",
      updatedAt: "2020-12-07T09:31:22.000Z"
    },
    {
      id: 912,
      name: "123",
      email: "123@123",
      password: "$2a$10$eHSHhg/V3oNLm59hWWVDyeE3JA6Ufyq7ztCvsqkMaUxk382df4Oq6",
      isAdmin: true,
      image: null,
      createdAt: "2020-11-29T17:19:13.000Z",
      updatedAt: "2020-12-04T20:56:32.000Z"
    },
    {
      id: 922,
      name: "111",
      email: "111@111",
      password: "$2a$10$Tm5YIdzQb7recZgv/A5ltuS.UtwwyovNqWYr45QfFpBk/vtU3Ppce",
      isAdmin: true,
      image: null,
      createdAt: "2020-11-29T17:42:08.000Z",
      updatedAt: "2020-12-04T20:56:32.000Z"
    },
    {
      id: 932,
      name: "王曉明",
      email: "123456@gmail.com",
      password: "$2a$10$.GiO.vIFy3LMym.YaOTyV.PqS5K95gNFajpFUAm7G0amWg0BgD6ka",
      isAdmin: true,
      image: null,
      createdAt: "2020-12-01T09:20:12.000Z",
      updatedAt: "2020-12-04T20:56:33.000Z"
    },
    {
      id: 942,
      name: "happy",
      email: "123@gmail.com",
      password: "$2a$10$OZJy/T5fYv.S4SfIeGFIYe8VetSmhtjK07yXAvUzafKUDv1HVe7yq",
      isAdmin: true,
      image: "https://i.imgur.com/NGYrvVa.jpeg",
      createdAt: "2020-12-03T08:45:00.000Z",
      updatedAt: "2020-12-04T20:56:33.000Z"
    },
    {
      id: 952,
      name: "ww",
      email: "ww@gmail.com",
      password: "$2a$10$G9O2Fl.NnccMWZ1ST5gxUem9nzv78/lJU4K0KOW3rcp4v1NjWQjkS",
      isAdmin: true,
      image: null,
      createdAt: "2020-12-04T16:22:02.000Z",
      updatedAt: "2020-12-04T20:56:34.000Z"
    },
    {
      id: 962,
      name: "Sean Yu",
      email: "SeanTestOne@gmail.com",
      password: "$2a$10$8iP/DigDL7g5vOFO7Jdfv.SYy7ofVxh4ZtZXh3TktY.2pNHV0GpOa",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-07T17:41:33.000Z",
      updatedAt: "2020-12-07T17:41:33.000Z"
    },
    {
      id: 972,
      name: "Sophia",
      email: "root1@example.com",
      password: "$2a$10$ZxC5MEXVqwU6gqWVdslwbeypzyu4gbI8lkRVL37Ra/a2gemNnhPDW",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T06:59:14.000Z",
      updatedAt: "2020-12-08T06:59:14.000Z"
    },
    {
      id: 982,
      name: "123",
      email: "root2@example.com",
      password: "$2a$10$SWsgjSRyZSjRh/0YVYPpoOkIM74mXdQe0/Fb1jEWRpT9FYNEtr6Zm",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:14:14.000Z",
      updatedAt: "2020-12-08T07:14:14.000Z"
    },
    {
      id: 992,
      name: "12345",
      email: "root3@example.com",
      password: "$2a$10$EVg0mHZtQZsCGuT4yf4bd.iTn/V6yJ9.ZMEd5TKfwi3PBh3E6ZRq2",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:15:43.000Z",
      updatedAt: "2020-12-08T07:15:43.000Z"
    },
    {
      id: 1002,
      name: "123456",
      email: "root5@example.com",
      password: "$2a$10$VNolC/rDOYdb7TVN7ajQBuBF4VfmeSiNEa0wtkUZjQNOvFLGjBAwi",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:16:26.000Z",
      updatedAt: "2020-12-08T07:16:26.000Z"
    },
    {
      id: 1012,
      name: "123456789",
      email: "root6@example.com",
      password: "$2a$10$xxDYyccXNvIzFpmfLUfhUuJuScoGy2iAv5KORtVLSszL1M4TL.7y2",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:17:59.000Z",
      updatedAt: "2020-12-08T07:17:59.000Z"
    },
    {
      id: 1022,
      name: "1234567890",
      email: "root66@example.com",
      password: "$2a$10$8Fx2CeuvAHk6FTVmwyOAwegqUc0nELCZtrtFftct9GmyGfLaYLPRi",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:21:47.000Z",
      updatedAt: "2020-12-08T07:21:47.000Z"
    },
    {
      id: 1032,
      name: "56",
      email: "root9@example.com",
      password: "$2a$10$db8C5hty5Z5ef4QI12bmk.o/53wjazv82FWYxy2WawFqdynjSgy7G",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:46:21.000Z",
      updatedAt: "2020-12-08T07:46:21.000Z"
    },
    {
      id: 1042,
      name: "12",
      email: "root10@example.com",
      password: "$2a$10$W3RwMkIgYgAs0ASt9Q7UQeqxwm3tlAXs3YkpR7pNydUhmAWzLFLke",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:50:50.000Z",
      updatedAt: "2020-12-08T07:50:50.000Z"
    },
    {
      id: 1052,
      name: "66",
      email: "root666@example.com",
      password: "$2a$10$08JfO5jMcfjZwQWjVVGtfeeQfy0QDucNUS9EVaD9Y67f3ExhcFevy",
      isAdmin: false,
      image: null,
      createdAt: "2020-12-08T07:54:15.000Z",
      updatedAt: "2020-12-08T07:54:15.000Z"
    }
  ]
};

const dummyUser = {
  currentUser: {
    id: 1,
    name: "root",
    email: "root@example.com",
    password: "$2a$10$0dBI.8S//NhlGeouBUbV3.oBDkdbbqXObuMJyuS.PHxjzdW/PvqYy",
    isAdmin: true,
    image: null,
    createdAt: "2020-11-23T10:08:45.000Z",
    updatedAt: "2020-12-04T20:56:30.000Z"
  }
};

export default {
  data() {
    return {
      users: [],
      currentUser: {}
    };
  },
  created() {
    this.fetchUser();
  },
  methods: {
    fetchUser() {
      // eslint-disable-next-line no-unused-vars
      const { users } = dummyData;
      const { currentUser } = dummyUser;
      this.users = users;
      this.currentUser = currentUser;
      console.log(users.length);
    },
    toggleUserRole(user) {
      if (user.isAdmin) {
        user.isAdmin = false;
      } else {
        user.isAdmin = true;
      }
    }
  }
};
</script>