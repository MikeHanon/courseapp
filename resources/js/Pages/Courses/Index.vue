<template>
  <app-layout>
    <template #header> Liste des formations </template>
    <div class="py-6 bg-gray-100" v-for="course in this.courseList" v-bind:key="course.id">
        <div class="mx-8 px-4 py-4 bg-white rounded shadow">
           <div class="text-sm text-gray-400">Mise en ligne par {{ course.user.name }} - <span
           class="text-gray-500 text-sm">{{course.participants}} participant<span v-if="parseInt(course.participants) > 1">s</span> </span> </div>
            <div class="flex justify-between items-center ">
                <div class="text-4xl ">{{course.title}}</div>
                <div class="text-sm text-gray-400">{{ course.episodes_count}} épisodes</div>
            </div>
            <div class="text-sm text-gray-500 ">{{course.description}}</div>
            <a :href="'course/' + course.id" class="bg-indigo-500 text-white px-2 py-1 text-sm mt-3 inline-block rounded hover:bg-indigo-700"> Voir la formation</a>
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

  data() {
      return{
          courseList: this.courses
      }
  },

  props: ["courses"],

  mounted() {
    console.log(this.courseList);
  },
};
</script>
