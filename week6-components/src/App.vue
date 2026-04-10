<script setup>
import { ref } from 'vue';
import PageHeader from './components/PageHeader.vue';
import MovieCard from './components/MovieCard.vue';

// 1. 심화 데이터 선언 : 더미 이미지 URL(picsum)과 다양한 평점 추가
const movies = ref([
  {
    id: 1, title: '인셉션', rating: 9.5,
    poster: 'https://picsum.photos/seed/inception/300/450',
    isHot: true, isNew: false, tags: ['SF', '명작']
  },
  {
    id: 2, title: '어바웃 타임', rating: 9.2,
    poster: 'https://picsum.photos/seed/abouttime/300/450',
    isHot: false, isNew: false, tags: ['로맨스', '인생영화']
  },
  {
    id: 3, title: '다크 나이트', rating: 9.8,
    poster: 'https://picsum.photos/seed/darkknight/300/450',
    isHot: true, isNew: true, tags: ['조커', '히어로']
  },
  {
    id: 4, title: '기생충', rating: 8.9,
    poster: 'https://picsum.photos/seed/parasite/300/450',
    isHot: false, isNew: true, tags: ['스릴러', '봉준호']
  }
]);
</script>

<template>
  <div class="container">
    <PageHeader title="🎬 6주 차 영화 추천 시스템" :count="movies.length" />
    <main class="movie-grid">
      <MovieCard v-for="m in movies" :key="m.id" :movie="m" />
    </main>
  </div>
</template>

<style scoped>
  .card { background: #fff; border-radius: 15px; overflow: hidden; box-shadow: 0 10px 20px rgba(0,0,0,0.1); transition: 0.3s; }
  .card:hover { transform: translateY(-10px); }
  .poster-area { position: relative; width: 100%; height: 350px; }
  .poster { width: 100%; height: 100%; object-fit: cover; }
  .recommend { position: absolute; top: 15px; left: 15px; padding: 5px 12px; border-radius: 5px; color: white; font-weight: bold; font-size: 0.85rem; }
  .best { background: #e74c3c; }
  .soso { background: #f39c12; }
  .poor { background: #95a5a6; }
  .content-area { padding: 20px; text-align: left; }
  .badge-area { margin-bottom: 10px; display: flex; gap: 5px; }
  .badge { font-size: 0.7rem; padding: 2px 6px; border-radius: 3px; color: white; }
  .hot { background: #ff4757; }
  .new { background: #2f3542; }
  h3 { margin: 0 0 10px 0; font-size: 1.3rem; color: #2f3542; }
  .rating { font-weight: bold; color: #7f8c8d; margin-bottom: 15px; }
  .tags { display: flex; gap: 5px; flex-wrap: wrap; }
  .tag-item { color: #3498db; font-size: 0.8rem; background: #f1f2f6; padding: 3px 8px; border-radius: 5px; }
  .container { 
  padding: 50px; 
max-width: 1100px; 
margin: 0 auto; 
background-color: #f1f2f6; 
min-height: 100vh; 
}
.movie-grid { 
display: grid; 
grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); 
gap: 35px; 
}
</style>