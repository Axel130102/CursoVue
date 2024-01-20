<script setup>
import { ref, computed } from 'vue' 
import BlogPost from './components/BlogPost.vue';
import PaginatePost from './components/PaginatePost.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';

const posts = ref([])

const postXpagina = 6

const inicio = ref(0)

const fin = ref(postXpagina)

const loading = ref(true)

const postFavorito = ref('')

const Next = () => {
  inicio.value = inicio.value + postXpagina
  fin.value = fin.value + postXpagina
}

const Back = () => {
  inicio.value = inicio.value - postXpagina
  fin.value = fin.value - postXpagina
}

const cambiarFavorito = (id, title) => {
  postFavorito.value = `${ id } - ${ title }` 
  }

const MaxLength = computed(() => posts.value.length)

fetch('https://jsonplaceholder.typicode.com/posts')
.then(res => res.json())
.then(data => {
  posts.value = data
})
.finally(() => {
  setTimeout(() => {
    loading.value = false
  }, 1000)
})


</script>

<template>

<LoadingSpinner v-if="loading"></LoadingSpinner>
<div class="bg-slate-400 dark:bg-slate-800 min-h-screen pb-32" v-else>
  <div class="flex flex-col items-center justify-center pt-10">


  <h1 class="text-2xl text-black dark:text-white"> Mi post Favorito: {{ postFavorito }}</h1>

  <PaginatePost 
    @Next="Next" 
    @Back="Back" 
    :inicio="inicio" 
    :fin="fin"
    :MaxLength="MaxLength"
    >
  </PaginatePost>

</div>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mx-10">
    <BlogPost
      v-for="post in posts.slice(inicio, fin)"
      :id="post.id"
      :title="post.title"
      :body="post.body"
      @cambiarFavoritoNombre="cambiarFavorito"
    ></BlogPost>
  </div>
</div>




  
</template>

