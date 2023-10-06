<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3'
import MyEditor from '@/Components/MyEditor.vue'

const props = defineProps({
  post: Object,
})
</script>

<template>
  <Head :title="post.title" />

  <div class="container mx-auto max-w-4xl my-8">
    <h2 class="text-2xl font-semibold">{{ post.title }}</h2>

    <div class="my-8 prose max-w-none" v-html="post.content"></div>
  </div>
</template>
