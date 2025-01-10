<template>
  <header class="bg-primary text-white py-4 fixed top-0 left-0 w-full z-10">
    <div class="container mx-auto flex justify-between items-center">
      <div class="flex flex-row items-center">
        <NuxtLink
          to="#"
          ><img
            src="/img/logo.png"
            alt="Logo"
            class="w-12 h-12 rounded-full mx-5 transform transition duration-300 hover:scale-110"
          />
        </NuxtLink>
        <h1 class="hidden lg:inline-block text-2xl font-bold">Pedro Vidal</h1>
      </div>
      <nav>
        <ul class="flex space-x-4 mx-10">
          <li>
            <NuxtLink to="#about" class="underline-animation"
              >Sobre mim</NuxtLink
            >
          </li>
          <li>
            <NuxtLink to="#experience" class="underline-animation"
              >Experiência</NuxtLink
            >
          </li>
          <li>
            <NuxtLink to="#projects" class="underline-animation"
              >Projetos</NuxtLink
            >
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.underline-animation {
  position: relative;
  display: inline-block;
}

.underline-animation::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: white;
  transition: width 0.3s ease;
}

.underline-animation:hover::after {
  width: 100%;
}
</style>
