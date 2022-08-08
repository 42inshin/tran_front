<script setup lang="ts">
import { onBeforeMount } from "@vue/runtime-core";
import axios from "axios";
import { RouterView } from "vue-router";
<<<<<<< HEAD
import AppNav from "./components/AppNav.vue"
=======
import AppNav from "./components/AppNav.vue";
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
import router from "./router";
import { useUserStore } from "./stores/user";
import Chat from "./components/Chat.vue";

let store = useUserStore();
<<<<<<< HEAD

</script>

<template>
  <div v-if="store.login"> {{ store.data.nickname }} 님 환영합니다!</div>
  <div v-else> 로그인이 필요합니다</div>
  <AppNav v-if="store.login"/>
  <RouterView />
    <!-- <Chat v-if="store.login"/> -->
=======
</script>

<template>
  <div v-if="store.login">{{ store.data.nickname }} 님 환영합니다!</div>
  <div v-else>로그인이 필요합니다</div>
  <AppNav v-if="store.login" />
  <RouterView />
<<<<<<<< HEAD:front/src/App.vue
  <Chat v-if="store.login" />
========
    <!-- <Chat v-if="store.login"/> -->
>>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf:ft_front/src/App.vue
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}
</style>
<<<<<<< HEAD

=======
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
