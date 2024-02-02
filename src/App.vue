<script setup>
import { reactive, computed } from 'vue'

const review = reactive({
  author: '',
  stars: null,
  text: '',
  photos: [],
  isRecomended: true
})

</script>

<template>
  <div>
    <input type="text">
  </div>
</template>

<style>
.container {
  width: 300px;
  height: 100vh;
  padding: 10px 15px;
  border: 2px solid salmon;
}
.container:hover{
  background-color: rgb(231, 238, 238);
  transition: .5s
}
input {
  margin-bottom: 35px;
}
ul {
  list-style: none;
}
ul li {
  font-size: 18px;
  font-weight: 700;
  letter-spacing: .5px;
  margin-bottom: 10px;
}
ul li:hover {
  color:coral;
  transition: .3s;
  transform: scaleX(1.07);
  border-bottom: 1px solid rgb(114, 50, 26);
}

.output {
  color: tomato;
  border-bottom: 1px solid springgreen;
  margin-bottom: 35px;
}
</style>


