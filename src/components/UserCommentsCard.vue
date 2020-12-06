<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ user.comments.length }}</strong> 已評論餐廳
    </div>
    <div class="card-body">
      <router-link
        v-for="commentItem in user.comments"
        :key="commentItem.id"
        :to="{ name: 'user', params: { id: commentItem.id } }"
      >
        <img :src=" commentItem.Restaurant.image | emptyImage" width="60" height="60" class="mr-1" />
      </router-link>
    </div>
  </div>
</template>

<script>
import { emptyImageFilter } from "./../utils/mixins";
export default {
  mixins: [emptyImageFilter],
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      profile: this.user
    };
  }
};
</script>