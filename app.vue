<script setup lang="ts">
const links = await usePagesFile("links");
</script>

<template>
  <main
    class="mx-auto max-w-prose grid gap-12 py-16 px-4 sm:py-24 sm:px-6 lg:px-8"
  >
    <NuxtRouteAnnouncer />

    <section
      v-for="section in links.sections"
      :key="section.heading"
      class="grid"
    >
      <h2 class="text-2xl font-bold">
        {{ section.heading }}
      </h2>

      <p v-if="section.description" class="mt-3 leading-relaxed">
        {{ section.description }}
      </p>

      <ul class="grid grid-cols-1 gap-2 mt-5">
        <li v-for="link in section.links" :key="link.title">
          <NuxtLink
            :to="link.url"
            class="flex items-center gap-2 py-3 rounded-lg border border-slate-400 hover:bg-blue-100 px-3 text-sm font-medium text-gray-900 transition duration-300 hover:scale-[1.02]"
          >
            <Icon
              v-if="link.icon"
              :name="link.icon"
              class="h-6 w-6 text-blue-950 flex-shrink-0"
            />
            {{ link.title }}
          </NuxtLink>
        </li>
      </ul>
    </section>
  </main>
</template>

<style>
body {
  @apply bg-blue-50;
}

main {
  font-family: Manrope;
  @apply text-blue-950;
}
</style>
