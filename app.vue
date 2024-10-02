<script setup lang="ts">
const links = await usePagesFile("links");
</script>

<template>
  <div>
    <NuxtRouteAnnouncer />
    <div v-for="section in links.sections" :key="section.heading">
      <h2 class="text-2xl font-bold">
        {{ section.heading }}
      </h2>

      <ul class="divide-y divide-gray-200">
        <li
          v-for="link in section.links"
          :key="link.title"
          class="flex items-center justify-between py-3"
        >
          <div class="flex items-center">
            <NuxtLink :to="link.url" class="text-sm font-medium text-gray-900">
              {{ link.title }}
            </NuxtLink>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
