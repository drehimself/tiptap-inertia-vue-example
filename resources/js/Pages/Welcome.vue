<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3'
import MyEditor from '@/Components/MyEditor.vue'

const props = defineProps({
  posts: Array,
})

const form = useForm({
  title: null,
  content: "<h1>Heading here</h1><p>I'm running Tiptap with Vue.js!!!! 🎉</p>",
})

function submitForm() {
  form.post('/', {
    preserveScroll: true,
    onSuccess: () => {
      alert('Form submission success!')
    },
  })
}
</script>

<template>
  <Head title="Welcome" />

  <div class="container mx-auto max-w-4xl my-8">
    <form @submit.prevent="submitForm" class="space-y-8">
      <input
        type="text"
        class="w-full border border-gray-400 p-2"
        v-model="form.title"
      />

      <MyEditor v-model="form.content" />
      <!-- <textarea
        name="content"
        id="content"
        cols="30"
        rows="10"
        class="w-full"
        v-model="form.content"
      ></textarea> -->

      <button type="submit" class="bg-blue-600 text-white p-2 rounded">
        Create Post
      </button>
    </form>

    <section class="my-8">
      <ul class="list-inside list-disc">
        <li v-for="post in posts" :key="post.id">
          <Link
            :href="route('post.show', post)"
            class="text-blue-600 hover:underline"
            >{{ post.title }}</Link
          >
        </li>
      </ul>
    </section>
  </div>
</template>
