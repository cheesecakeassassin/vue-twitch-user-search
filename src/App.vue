<template>
  <div class="w-screen h-screen overflow-hidden">
    <div class="max-w-screen-lg mx-auto bg-neutral-800 rounded-lg mt-10 p-10 font-['Inter']">
      <div class="text-center">
        <h1 class="text-4xl font-bold">Twitch User Search</h1>
        <p class="mt-2">
          Find the most important stats about your favorite creator using this
          tool.
        </p>
      </div>

      <div class="flex mt-5">
        <UserSearch class="mx-auto" />
      </div>

      <div class="text-center mt-5">
        Created by
        <a
          class="text-orange-500"
          href="https://github.com/cheesecakeassassin"
          target="_blank"
          rel="noreferrer noopener"
        >
          cheesecakeassassin 🎅
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import UserSearch from "@/components/UserSearch.vue";
</script>

<style>
@import "@/assets/base.css";
</style>
