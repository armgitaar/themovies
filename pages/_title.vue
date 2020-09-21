<template>
  <div class="py-10">
    <header>
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h1 class="text-3xl font-bold leading-tight text-gray-900">
          {{ movie.title }}
        </h1>
      </div>
    </header>
    <main>
      <div class="flex max-w-7xl mx-auto sm:px-6 lg:px-8 mt-4">
        <div>
          <img class="w-full" :src="movie.poster_image" alt="">
        </div>
        <div class="px-12 max-w-5xl">
          <div>
            <dl>
              <div class="sm:grid sm:grid-cols-3 sm:gap-4">
                <dt class="text-sm leading-5 font-medium text-gray-700">
                  Released
                </dt>
                <dd class="mt-1 text-sm leading-5 text-gray-900 sm:mt-0 sm:col-span-2">
                  {{ movie.release_year }}
                </dd>
              </div>
              <div class="mt-8 sm:grid sm:mt-5 sm:grid-cols-3 sm:gap-4 sm:border-t sm:border-gray-200 sm:pt-5">
                <dt class="text-sm leading-5 font-medium text-gray-700">
                  Genres
                </dt>
                <dd class="mt-1 text-sm leading-5 text-gray-900 sm:mt-0 sm:col-span-2">
                  {{ movie.genres }}
                </dd>
              </div>
              <div class="mt-8 sm:grid sm:mt-5 sm:grid-cols-3 sm:gap-4 sm:border-t sm:border-gray-200 sm:pt-5">
                <dt class="text-sm leading-5 font-medium text-gray-700">
                  Top Billed
                </dt>
                <dd class="mt-1 text-sm leading-5 text-gray-900 sm:mt-0 sm:col-span-2">
                  {{ movie.top_billed }}
                </dd>
              </div>
              <div class="mt-8 sm:grid sm:mt-5 sm:grid-cols-3 sm:gap-4 sm:border-t sm:border-gray-200 sm:pt-5">
                <dt class="text-sm leading-5 font-medium text-gray-700">
                  Plot
                </dt>
                <dd class="mt-1 text-sm leading-5 text-gray-900 sm:mt-0 sm:col-span-2">
                  {{ movie.movie_description }}
                </dd>
              </div>
              <div class="mt-8 sm:grid sm:mt-5 sm:grid-cols-3 sm:gap-4 sm:border-t sm:border-gray-200 sm:pt-5">
                <dt class="text-sm leading-5 font-medium text-gray-700">
                  Review
                </dt>
                <dd class="mt-1 text-sm leading-5 text-gray-900 sm:mt-0 sm:col-span-2">
                  {{ movie.movie_review }}
                </dd>
              </div>
            </dl>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    props: {
      movie: Array,
    },
    async asyncData({ params }) {
      const { data } = await axios.get(`https://api.leanbranch.com/movies/${params.title}`)
      return {
        movie: data
      }
    },
  }
</script>

<style>
</style>
