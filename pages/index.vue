<template>
  <div class="bg-gray-100 min-h-screen">
    <section
      class="flex justify-center items-center py-40 bg-primary text-white break-words w-full min-h-screen"
    >
      <h1 class="text-lg lg:text-3xl font-bold items-center">
        <span class="typewriter">{{ currentQuote }}</span>
        <span class="caret"></span>
      </h1>
      <NuxtLink
        to="#about"
        class="absolute bottom-5 flex justify-center w-full"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          class="w-8 h-8 text-white animate-bounce"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M5 10l7 7 7-7"
          ></path>
        </svg>
      </NuxtLink>
    </section>

    <section
      id="about"
      class="flex items-center justify-center space-x-8 bg-white p-8 py-16 mb-32 rounded-xl shadow-2xl mx-auto min-h-screen"
    >
      <div class="w-1/3 flex justify-center">
        <img
          src="/img/profile.jpg"
          alt="Pedro Vidal"
          class="rounded-full w-60 h-60 object-cover transform transition duration-300 hover:scale-110"
        />
      </div>
      <div class="w-3/6">
        <h2 class="text-3xl font-bold text-primary mb-6 tracking-wide">
          Sobre Mim
        </h2>
        <p class="text-gray-700 text-lg leading-relaxed">
          Desenvolvedor mobile e front-end especializado em React (Native e
          Next.js). Participei do desenvolvimento de aplicativos como o 156
          Caraguatatuba e o SAEG, impactando a vida de milhares de usuários.
          Sempre em busca de novas conexões e oportunidades para crescer no
          mundo do desenvolvimento de software. Vamos nos conectar!
        </p>
      </div>
    </section>

    <section id="experience" class="py-16 bg-gray-50 shadow-2xl min-h-screen">
      <div class="container mx-auto p-12">
        <h2 class="text-3xl font-bold text-gray-800 mb-8">Experiência</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <ExperienceCard
            v-for="experience in experiences"
            :key="experience.title"
            :title="experience.title"
            :description="experience.description"
            :company="experience.company"
            :period="experience.period"
            :image="experience.image"
          />
        </div>
      </div>
    </section>

    <section id="projects" class="py-16 container mx-auto min-h-screen">
      <div class="container p-12">
        <h1 class="text-3xl font-bold">Projetos</h1>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 mt-8">
          <ProjectCard
            v-for="project in projects"
            :key="project.title"
            :title="project.title"
            :description="project.description"
            :image="project.image"
            :link="project.link"
          />
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({
  title: "Pedro Vidal",
});
// Importar dados
import { experiences } from "~/data/experiences";
import { projects } from "~/data/projects";

// Lógica por trás das citações
const quotes = [
  `"A good captain is great only if he has a great team."`,
  `"Coding is like poetry, it should be short and concise."`,
  `"Make it work, make it right, make it fast."`,
  `"First, solve the problem. Then, write the code."`,
];

const currentQuote = ref("");
const currentIndex = ref(0);
let typingInterval;
let deletingInterval;
let lastQuoteIndex = -1;

const changeQuote = () => {
  let randomIndex;

  do {
    randomIndex = Math.floor(Math.random() * quotes.length);
  } while (randomIndex === lastQuoteIndex);

  lastQuoteIndex = randomIndex;

  let currentQuoteText = quotes[randomIndex];

  const deleteQuote = () => {
    if (currentQuote.value.length > 0) {
      currentQuote.value = currentQuote.value.slice(0, -1);
      currentIndex.value--;
      return;
    }
    clearInterval(deletingInterval);
    typingQuote(currentQuoteText);
  };

  deletingInterval = setInterval(deleteQuote, 25);
};

const typingQuote = (quoteText) => {
  let text = quoteText;

  const typeQuote = () => {
    if (currentIndex.value < text.length) {
      currentQuote.value += text[currentIndex.value];
      currentIndex.value++;
      return;
    }
    clearInterval(typingInterval);
    setTimeout(changeQuote, 10000);
  };

  typingInterval = setInterval(typeQuote, 50);
};

// Rodar ao mount
onMounted(() => {
  changeQuote();
});
</script>

<style scoped>
.typewriter {
  display: inline-block;
  font-family: monospace;
  white-space: nowrap;
  overflow: hidden;
  padding-right: 5px;
}

.caret {
  display: inline-block;
  width: 2px;
  height: 1.5em;
  background-color: white;
  animation: blinkCaret 0.7s step-end infinite;
}

.cursor-bg {
  transition: transform 0.1s ease-out;
}

@keyframes blinkCaret {
  50% {
    background-color: transparent;
  }
}
</style>
