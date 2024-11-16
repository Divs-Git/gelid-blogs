<template>
  <div class="main">
    <div class="loader" v-if="isLoading">
      <PulseLoader :loading="isLoading" size="24px" />
    </div>
    <div class="blog-container" v-else>
      <div class="blogs" v-if="!isError">
        <div v-for="blog in blogList" :key="blog.id">
          <BlogList :blog="blog" />
        </div>
      </div>
      <div class="error" v-else>
        {{ error }}
      </div>
    </div>
  </div>
</template>

<script setup>
import PulseLoader from "vue-spinner/src/PulseLoader.vue";
import BlogList from "@/components/BlogList.vue";
import axios from "axios";
import { onMounted, ref } from "vue";

const blogList = ref([]);
const isError = ref(false);
const error = ref("");
const url = ref("http://localhost:8080/blogs");
const isLoading = ref(false);

const getBlogs = async () => {
  isLoading.value = true;
  isError.value = false;
  try {
    const res = await axios.get(url.value);
    blogList.value = res.data;
    console.log(blogList.value);
  } catch (err) {
    isError.value = true;
    error.value = err.response.data;
  }
  isLoading.value = false;
};

onMounted(() => {
  getBlogs();
});
</script>

<style scoped>
.loader {
  z-index: 1000;
  width: 60%;
  margin: 300px auto;
}

.blog-container {
  width: 70%;
  margin: 50px auto;
}
</style>
