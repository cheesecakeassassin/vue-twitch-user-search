<script setup>
import UserSearch from "@/components/UserSearch.vue";
</script>

<template>
  <header>
    <h1 class="title">Twitch User Search</h1>
  </header>
  <UserSearch />
  <footer>
    <p>
      Created by
      <a
        href="https://github.com/cheesecakeassassin"
        target="_blank"
        rel="noreferrer noopener"
      >
        cheesecakeassassin 🎅
      </a>
    </p>
  </footer>
</template>

<style>
@import "@/assets/base.css";

p {
  text-align: center;
}

a {
  text-decoration: none;
  color: rgb(255, 111, 89);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: rgba(255, 111, 89, 0.2);
  }
}

.title {
  font-size: 54px;
  text-align: center;
  margin-top: 50px;
}
</style>
