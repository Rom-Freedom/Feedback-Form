<script setup>
import { reactive, computed } from "vue";

const review = reactive({
  author: "",
  stars: null,
  text: "",
  photo: null,
  isRecomended: true,
});

const previewFilePath = computed(() => {
  if (review.photo) {
    return URL.createObjectURL(review.photo)
  }
  return '#'
})

const stars = [1, 2, 3, 4, 5];

const submit = () => {
  console.log("submit!");
};

const uploadFile = (e) => {
  const [file] = e.target.files;
  review.photo = file;
}
</script>

<template>
  <form @submit.prevent.stop="submit" class="container pt-5 pb-5">
    <input
      type="text"
      v-model="review.author"
      placeholder="Ведите Ваше имя"
      class="form-control mb-3"
    />

    <textarea
      v-model="review.text"
      rows="3"
      class="form-control mb-3"
      placeholder="Оставьте отзыв"
    ></textarea>

    <h4>Оценка</h4>
    <div v-for="star in stars" :key="star" class="form-check mb-3">
      <input
        class="form-check-input"
        type="checkbox"
        v-model="review.stars"
        :true-value="star"
        :false-value="null"
        :id="`star${star}`"
      />
      <label class="form-check-label" :for="`star${star}`">
        {{ star }}
      </label>
    </div>

    <div class="mb-3">
      <label class="form-label">Фото</label>
      <input
        class="form-control"
        type="file" 
        @change="uploadFile"
      />

      <img :src="previewFilePath" alt="preview img" class="w-100 mt-2">
    </div>

    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        id="adv1"
        v-model="review.isRecomended"
        :value="false"
      />
      <label class="form-check-label" for="adv1"> Не советую </label>
    </div>

    <!-- Form Check -->
    <div class="form-check mb-3">
      <input
        class="form-check-input"
        type="radio"
        id="adv2"
        v-model="review.isRecomended"
        :value="true"
      />
      <label class="form-check-label" for="adv2"> Советую </label>
    </div>
    <!-- Form Check -->

    <button class="btn btn-primary">Отправить</button>
  </form>
</template>

<style></style>
