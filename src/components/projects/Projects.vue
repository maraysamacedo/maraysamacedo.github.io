<template>
  <section id="skills" class="container-skills text-center py-5 mt-5">
    <h2 class="fw-bold mb-5" style="color: #ff4081;">Projetos</h2>
    <div id="carouselExampleIndicators" class="carousel slide">
      <!-- Indicadores do Carousel -->
      <div class="carousel-indicators">
        <button
            v-for="(group, index) in groupedCards"
            :key="index"
            type="button"
            data-bs-target="#carouselExampleIndicators"
            :data-bs-slide-to="index"
            :class="{ active: index === 0 }"
            :aria-label="'Slide ' + (index + 1)"
        ></button>
      </div>

      <!-- Slides do Carousel -->
      <div class="carousel-inner">
        <div
            v-for="(group, index) in groupedCards"
            :key="index"
            :class="['carousel-item', { active: index === 0 }]"
        >
          <div class="d-flex justify-content-center gap-4 mb-5">
            <div
                v-for="(card, cardIndex) in group"
                :key="cardIndex"
                class="card"
                style="width: 18rem;"
            >
              <img :src="card.src" class="card-img-top" :alt="card.alt" />
              <div class="card-body">
                <h5 class="card-title">{{ card.title }}</h5>
                <p class="card-text">{{ card.description }}</p>
                <a :href="card.link" class="btn btn-primary">Ver Projeto</a>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Controles do Carousel -->
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Anterior</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Próximo</span>
      </button>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref, computed } from 'vue';
import 'bootstrap/dist/css/bootstrap.min.css'; // Importa o CSS do Bootstrap
import { Carousel } from 'bootstrap'; // Importa o componente Carousel

// Array de cards com informações
const cards = ref([
  {
    src: new URL('../../assets/img1.jpg', import.meta.url).href,
    alt: 'Imagem 1',
    title: 'Projeto 1',
    description: 'Descrição do Projeto 1.',
    link: '#',
  },
  {
    src: new URL('../../assets/img2.jpg', import.meta.url).href,
    alt: 'Imagem 2',
    title: 'Projeto 2',
    description: 'Descrição do Projeto 2.',
    link: '#',
  },
  {
    src: new URL('../../assets/img3.jpg', import.meta.url).href,
    alt: 'Imagem 3',
    title: 'Projeto 3',
    description: 'Descrição do Projeto 3.',
    link: '#',
  },
  {
    src: new URL('../../assets/img4.jpg', import.meta.url).href,
    alt: 'Imagem 4',
    title: 'Projeto 4',
    description: 'Descrição do Projeto 4.',
    link: '#',
  },
  {
    src: new URL('../../assets/img5.jpg', import.meta.url).href,
    alt: 'Imagem 5',
    title: 'Projeto 5',
    description: 'Descrição do Projeto 5.',
    link: '#',
  },
  {
    src: new URL('../../assets/img6.jpg', import.meta.url).href,
    alt: 'Imagem 6',
    title: 'Projeto 6',
    description: 'Descrição do Projeto 6.',
    link: '#',
  },
  {
    src: new URL('../../assets/img6.jpg', import.meta.url).href,
    alt: 'Imagem 7',
    title: 'Projeto 7',
    description: 'Descrição do Projeto 7.',
    link: '#',
  },
  {
    src: new URL('../../assets/img6.jpg', import.meta.url).href,
    alt: 'Imagem 8',
    title: 'Projeto 8',
    description: 'Descrição do Projeto 8.',
    link: '#',
  },
]);

// Agrupa os cards em grupos de 3
const groupedCards = computed(() => {
  const groups = [];
  for (let i = 0; i < cards.value.length; i += 4) {
    groups.push(cards.value.slice(i, i + 4));
  }
  return groups;
});

// Inicializa o carrossel corretamente ao montar o componente
onMounted(() => {
  const carouselElement = document.getElementById('carouselExampleIndicators');
  if (carouselElement) {
    new Carousel(carouselElement, {
      interval: 3000, // Troca automática de slides a cada 3 segundos
      wrap: true, // Habilita a rotação infinita
    });
  }
});
</script>

<style scoped>
/* Estilos personalizados */
.container-skills {
  padding: 60px 0; /* Espaçamento interno */
}

.carousel-item {
  padding: 20px;
}

.card {
  border-radius: 10px; /* Arredonda as bordas do card */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Adiciona uma sombra suave */
}

.card-img-top {
  border-top-left-radius: 10px; /* Arredonda as bordas superiores da imagem */
  border-top-right-radius: 10px;
  height: 200px; /* Altura fixa para a imagem */
  object-fit: cover; /* Mantém a proporção e corta a imagem se necessário */
}

.card-body {
  padding: 20px;
}

.btn-primary {
  background-color: #ff4081; /* Cor rosa vibrante */
  border: none;
  transition: background-color 0.3s ease;
}

.btn-primary:hover {
  background-color: #e91e63; /* Cor rosa mais escura ao passar o mouse */
}
</style>