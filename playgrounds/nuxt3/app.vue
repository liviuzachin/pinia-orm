<template>
  <div>Nuxt module playground!</div>
</template>

<script setup  lang="ts">
import User from './models/User'
import { useRepo } from 'pinia-orm'
onBeforeMount(() => {
  const userRepo = useRepo(User)
  const users = userRepo.save([
    {
      id: 1,
      email: 'test@test.de',
      name: 'test',
      todos: [
        {
          title: 'Hoho',
        },
        {
          title: 'Blub',
        },
      ],
    },
  ])
  console.log(userRepo.with('todos').get())
})

</script>
