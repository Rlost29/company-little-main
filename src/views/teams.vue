<script lang="ts">
import { defineComponent } from 'vue'

import axios from 'axios'

interface User {
  name: {
    first: string
    last: string
  }
  email: string
  picture: {
    large: string
  }
  login: {
    uuid: string
  }
}

export default defineComponent({
  name: 'RandomUsers',
  data() {
    return {
      loading: true,
      error: '',
      users: [] as User[]
    }
  },
  async created() {
    try {
      const response = await axios.get('https://randomuser.me/api/?results=5')
      this.users = response.data.results
      this.loading = false
    } catch (error) {
      this.error = 'Failed to fetch users'
      this.loading = false
    }
  }
})
</script>
<template>
  <section>
    <div class="container px-6 py-10 mx-auto">
      <h1 class="text-2xl font-semibold text-center text-gray-800 capitalize lg:text-3xl">
        The Executive Team
      </h1>

      <div class="flex justify-center mx-auto mt-6">
        <span class="inline-block w-40 h-1 bg-blue-500 rounded-full"></span>
        <span class="inline-block w-3 h-1 mx-1 bg-blue-500 rounded-full"></span>
        <span class="inline-block w-1 h-1 bg-blue-500 rounded-full"></span>
      </div>

      <p class="max-w-2xl mx-auto mt-6 text-center text-gray-500">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo incidunt ex placeat modi magni
        quia error alias, adipisci rem similique, at omnis eligendi optio eos harum.
      </p>

      <div class="grid grid-cols-1 gap-8 mt-8 xl:mt-16 md:grid-cols-2 xl:grid-cols-4">
        <div v-for="user in users" :key="user.login.uuid">
          <div
            class="flex flex-col items-center p-8 transition-colors duration-300 transform cursor-pointer group hover:bg-blue-600 rounded-xl"
          >
            <img
              class="object-cover w-32 h-32 rounded-full ring-4 ring-gray-300"
              :src="user.picture.large"
              :alt="`${user.name.first} ${user.name.last}`"
            />

            <h1 class="mt-4 text-2xl font-semibold text-gray-700 capitalize group-hover:text-white">
              {{ user.name.first }} {{ user.name.last }}
            </h1>

            <p class="mt-2 text-gray-500 capitalize group-hover:text-gray-300">
              {{ user.email }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
