<template>
  <div class="post-detail">
    <h1>This is a PostDetail Page</h1>
    <p>Display the content of post with id of {{ $route.params.id }} here!</p>
    <div>
      <button @click="showPostId">Show post id</button>
    </div>
    <div>
      <button @click="goHome3Seconds">Go Home in 3 seconds</button>
    </div>
    <div>
      <button @click="goToFirstPost">Go to First Post</button>
    </div>
    <p><RouterLink to="/posts">&lt; Back</RouterLink></p>
  </div>
</template>

<script setup>
/*
  imports
  */
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();

const showPostId = () => {
  alert(`The ID of this post is: ${route.params.id}`);
};

const goHome3Seconds = () => {
  setTimeout(() => {
    router.push({ name: "home" });
  }, 3000);
};

const goToFirstPost = () => {
  router.push({
    name: "postDetail",
    params: {
      id: "id1",
    },
  });
};
</script>
