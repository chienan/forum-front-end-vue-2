<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ user.favoritedRestaurants.length }}</strong> 收藏的餐廳
    </div>
    <div class="card-body">
      <router-link
        v-for="favRes in user.favoritedRestaurants"
        :key="favRes.id"
        :to="{ name: 'user', params: { id: favRes.id } }"
      >
        <img :src="favRes.image" width="60" height="60" class="mr-1" />
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
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