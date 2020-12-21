<template>
  <div>
    <h2 class="my-4">所有評論：</h2>

    <div v-for="comment in restaurantComments" :key="comment.id">
      <blockquote class="blockquote mb-0">
        <button
          v-if="currentUser.isAdmin"
          @click.stop.prevent="handleDeleteButtonClick(comment.id)"
          type="button"
          class="btn btn-danger float-right"
        >Delete</button>
        <h3>
          <a href="#">{{comment.User.name}}</a>
        </h3>
        <p>{{comment.text}}</p>
        <footer class="blockquote-footer">{{comment.createdAt | fromNow}}</footer>
      </blockquote>
      <hr />
    </div>
  </div>
</template>

<script>
import { fromNowFilter } from "../utils/mixins";
import { mapState } from "vuex";
import commentsAPI from "./../apis/comments";
import { Toast } from "./../utils/helpers";

// const dummyUser = {
//   currentUser: {
//     id: 1,
//     name: "管理者",
//     email: "root@example.com",
//     image: "https://i.pravatar.cc/300",
//     isAdmin: true
//   },
//   isAuthenticated: true
// };

export default {
  mixins: [fromNowFilter],
  props: {
    restaurantComments: {
      type: Array,
      required: true
    }
  },
  // data() {
  //   return {
  //     currentUser: dummyUser.currentUser
  //   };
  // },
  computed: {
    ...mapState(["currentUser"])
  },
  methods: {
    async handleDeleteButtonClick(commentId) {
      try {
        this.isProcessing = true;
        const { data } = await commentsAPI.delete({ commentId });
        if (data.status === "error") {
          throw new Error(data.message);
        }
        this.$emit("after-delete-comment", commentId);
        Toast.fire({
          icon: "success",
          title: "移除評論成功"
        });
        this.isProcessing = false;
      } catch (error) {
        console.error(error.message);
        this.isProcessing = false;
        Toast.fire({
          icon: "error",
          title: "無法移除評論，請稍後再試"
        });
      }
      // handleDeleteButtonClick(commetId) {
      //   console.log("handleDeleteButtonClick", commetId);
      //   // TODO: 請求 API 伺服器刪除 id 為 commentId 的評論
      //   // 觸發父層事件 - $emit( '事件名稱' , 傳遞的資料 )
      //   this.$emit("after-delete-comment", commetId);
      // }
    }
  }
};
</script>