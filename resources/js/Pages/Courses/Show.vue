<template>
  <app-layout>
    <template #header> {{ course.title }} </template>
    <div class="mx-8 px-4 py-4">
      <div class="text-2xl text-gray-500">
        {{ this.courseShow.episodes[this.currentKey].title }}
      </div>
      <iframe
        class="w-full h-screen"
        :src="this.courseShow.episodes[this.currentKey].video_url"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
      <div class="text-sm text-gray-700">
        {{ this.courseShow.episodes[this.currentKey].description }}
      </div>

      <div class="mt6">
        <ul
          v-for="(episode, index) in this.courseShow.episodes"
          v-bind:key="episode.id"
        >
          <li class="mt-3">
            Episode n°{{ index + 1 }} - {{ episode.title }}
            <button
              class="text-gray-700 focus:text-indigo-500 focus:outline-none"
              @click="switchEpisode(index)"
            >
              voir l'épisode
            </button>
          </li>
        </ul>
      </div>
    </div>
  </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";

export default {
  components: {
    AppLayout,
  },

  props: ["course"],

  data() {
    return {
      courseShow: this.course,
      currentKey: 0,
    };
  },

  methods: {
    switchEpisode(index) {
      this.currentKey = index;

      window.scrollTo({
          top: 0,
          left: 0,
          behavior: 'smooth'
      })
    },
  },

  mounted() {
    //
  },
};
</script>
