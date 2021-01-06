<template>
  <app-layout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Dashboard
      </h2>
    </template>

    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <form
          class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 flex flex-col"
          @submit.prevent="submit"
        >
          <div class="mb-4">
            <label
              class="block text-grey-darker text-sm font-bold mb-2"
              for="title"
            >
              titre de la formation
            </label>
            <input
              class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker"
              id="title"
              type="text"
              v-model="form.title"
            />
          </div>
          <div class="mb-4">
            <label
              class="block text-grey-darker text-sm font-bold mb-2"
              for="description"
            >
              description de la formation
            </label>
            <textarea
              class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker"
              id="description"
              type="text"
              v-model="form.description"
            ></textarea>
          </div>

          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline w-48"
            type="submit"
          >
            créer ma formation
          </button>
        </form>
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
    return {
      form: {
        title: null,
        description: null,
      },
    };
  },

  methods: {
    submit() {
      this.$inertia.post("/courses", this.form);
    },
  },
};
</script>
