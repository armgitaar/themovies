<template>
  <div class="py-10">
    <header>
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h1 class="text-3xl font-bold leading-tight text-gray-900">
          Movies
        </h1>
      </div>
    </header>
    <main>
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 mt-4">
        <div class="bg-white shadow overflow-hidden sm:rounded-md">
          <ul>
            <li v-for="movie in movies">
              <nuxt-link :to="`/${movie.id}`" class="block hover:bg-gray-50 focus:outline-none focus:bg-gray-50 transition duration-150 ease-in-out">
                <div class="flex items-center px-4 py-4 sm:px-6">
                  <div class="min-w-0 flex-1 flex items-center">
                    <div class="flex-shrink-0">
                      <img class="h-12" :src="movie.poster_image" alt="">
                    </div>
                    <div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
                      <div>
                        <div class="text-sm leading-5 font-medium text-indigo-600 truncate">{{ movie.title }}</div>
                        <div class="mt-2 flex items-center text-sm leading-5 text-gray-700">
                          {{ movie.release_year }} | {{ movie.genres }}
                        </div>
                      </div>
                      <div class="hidden md:block">
                        <div>
                          <div class="text-sm leading-5 text-gray-900">
                            {{ movie.top_billed }}
                          </div>
                          <div class="mt-2 flex items-center text-sm leading-5 text-gray-600 truncate ...">
                            {{ movie.movie_description }}
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                  <div>
                    <svg class="h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
                      <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
                    </svg>
                  </div>
                </div>
              </nuxt-link>
            </li>
          </ul>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    asyncData({ params }) {
      return axios.get(`https://backend.leanbranch.com/movies`).then(res => {
        return { movies: res.data }
      })
    }
  }
</script>

<style>
</style>
