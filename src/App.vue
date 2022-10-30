<script>
import { RouterLink, RouterView } from 'vue-router'
import {ref} from 'vue'
import Form from './components/Form.vue'
import List from './components/List.vue'

export default {
  components: { Form, List },
  setup() {
    const items = ref([
      {
        id: 1,
        body: 'Админ на месте',
        likes: 9999,
        avatar: `https://avatars.dicebear.com/api/male/38.svg`,
        date: new Date(Date.now()).toLocaleString()
      },
    ])
    const handleSubmit = item => items.value.push(item)
    return {
      items,
      handleSubmit
    }
  }
}
</script>

<template>
   <div class="wrapper">
    <!-- header -->
    <div class="wrapper-content">
      <div class="view">
        <div class="container">
          <Form @onSubmit="handleSubmit" />
          <List :items="items" />
        </div>
      </div>
    </div>
    <!-- footer -->
  </div>

  <RouterView />
</template>

<style scoped>

</style>
