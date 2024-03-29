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
  <section class="bgcompany">
    <div class="relative grid w-full bg-gray-900/40 h-96 lg:h-[32rem] place-items-center">
      <div class="flex flex-col items-center mx-auto text-center">
        <h1 class="text-4xl font-semibold text-white uppercase md:text-6xl">About Us</h1>

        <p class="mt-6 text-lg leading-5 text-white">
          CryTech, we are dedicated to revolutionizing the way businesses manage their digital
          infrastructure.
        </p>
      </div>
    </div>
  </section>

  <section class="py-12 bg-gray-100">
    <div class="container mx-auto">
      <h2 class="text-3xl font-semibold text-center text-gray-800 mb-8">Company History</h2>
      <div class="max-w-3xl mx-auto">
        <p class="text-lg text-gray-700">
          Founded in 2020, CryTech has been leading the way in cloud server solutions and website
          development since its inception. From humble beginnings, our company has evolved into a
          respected authority in the technology industry, serving clients with dedication and
          innovation.
        </p>
        <p class="mt-4 text-lg text-gray-700">
          Over the years, CryTech has achieved numerous milestones that have shaped our journey and
          contributed to our success. From the successful deployment of large-scale cloud
          infrastructure projects to the development of innovative website solutions, each
          achievement reflects our commitment to excellence and our relentless pursuit of customer
          satisfaction.
        </p>
        <p class="mt-4 text-lg text-gray-700">
          As we look to the future, CryTech remains dedicated to providing cutting-edge technology
          solutions tailored to our clients' needs. We are excited about the opportunities that lie
          ahead and are committed to continuing our legacy of innovation, quality, and customer
          satisfaction.
        </p>
      </div>
    </div>
    <div class="py-12 container mx-auto">
      <h2 class="text-3xl font-semibold text-center text-gray-800 mb-8">Culture at CryTech</h2>
      <div class="max-w-3xl mx-auto space-y-6">
        <p class="text-lg text-gray-700 leading-relaxed">
          At CryTech, our culture is the cornerstone of our success. We foster an environment that
          values innovation, collaboration, and continuous learning.
        </p>
        <p class="text-lg text-gray-700 leading-relaxed">
          <strong>Innovation:</strong> We encourage creativity and curiosity, empowering our team
          members to think outside the box and develop cutting-edge solutions for our clients.
        </p>
        <p class="text-lg text-gray-700 leading-relaxed">
          <strong>Collaboration:</strong> We believe in the power of teamwork. We foster open
          communication, mutual respect, and diversity, knowing that it strengthens our ability to
          achieve our goals.
        </p>
        <p class="text-lg text-gray-700 leading-relaxed">
          <strong>Continuous Learning:</strong> In a fast-paced industry, learning never stops. We
          provide opportunities for professional development and growth, ensuring that our team
          members are always up-to-date with the latest trends and technologies.
        </p>
        <p class="text-lg text-gray-700 leading-relaxed">
          <strong>Work-Life Balance:</strong> We prioritize the well-being of our team members. We
          offer flexible work arrangements and wellness programs to support a healthy work-life
          balance.
        </p>
        <p class="text-lg text-gray-700 leading-relaxed">
          <strong>Customer-Centric Approach:</strong> Our customers are at the center of everything
          we do. We listen to their needs, anticipate their challenges, and go above and beyond to
          ensure their success.
        </p>
        <p class="text-lg text-gray-700 leading-relaxed">
          <strong>Fun and Inclusivity:</strong> While we take our work seriously, we also know how
          to have fun. We organize team-building activities and social events to create a positive
          and inclusive work environment where everyone feels valued and supported.
        </p>
      </div>
    </div>
  </section>

  <!--  -->
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
<style scoped>
.bgcompany {
  background-image: url('https://images.unsplash.com/photo-1556761175-b413da4baf72?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1374&q=80');
}
</style>
