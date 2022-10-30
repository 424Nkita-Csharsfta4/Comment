<template>
  <form @submit.prevent="onSubmit">
    <textarea class="inp" v-model="body" required placeholder="Оставь свой коментарий" />
    <button class="btn btnTweet" type="submit">Опубликовать пост</button>
  </form>
</template>

<script>
import { ref } from 'vue'
export default {
  emits: ['onSubmit'],
  setup(_, { emit }) {
    const body = ref('')
    const onSubmit = () => {
      emit('onSubmit', {
        id: Math.round(Math.random() * 30),
        avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
        body: body.value,
        likes: 0,
        date: new Date(Date.now()).toLocaleString()
      })
      body.value = ''
    }
    return { body, onSubmit }
  }
}
</script>
<style>
.btn.btnTweet{
  width: 200px;
  height: 50px;
  border: none;
  background: rgb(78, 74, 74); 
  border-radius: 10px;
  margin-top: 2em;
}
.inp{
  width: 500px;
  height: 200px;
  border-radius: 10px;
  border: none;
  margin-bottom: 2em;
}
.btn.btnTweet:hover{
  color: rgb(243, 13, 13);
  background: rgb(113, 108, 108);
  transition: 0.4s ease-in-out;
}
</style>