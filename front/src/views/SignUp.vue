<script setup lang="ts">
import router from '@/router';
import { useUserStore } from '@/stores/user';
import axios from 'axios';
import { ref } from 'vue';
import { useCookies } from 'vue3-cookies';

const count = ref()
let message:any = ref();
let nickcheck:any = ref("");
const { cookies } = useCookies();

async function checkValid() {
  let nickname = message;
  await axios
    .post("/api/users/nickname", { nickname: nickname.value }, 
    { 
      headers: {
        Authorization: `Bearer ` + cookies.get('jwt'),
      }
    })
    .then(
      (res) => {
          console.log(res);
          useUserStore().data.nickname = nickname.value;
          router.push('/test');
        }
    )
    .catch(
      (error) => {
          console.log(error);
          nickcheck = "존재하는 닉네임 입니다.";
    });
}
</script>

<style >
@import '../assets/css/signup.css';
</style>

<template>
<link rel="shortcut icon" href="#">
  <main>
    <body>
  <div>
    <h1>닉네임 입력해라</h1>
    <p>넌 닉네임 설정이 안되있어 닉네임 설정을 해야해.</p>
    <hr>
    <label for="nickname"><b>nickname </b></label>
    <input v-model="message" placeholder="Enter nickname" name="nickname">
    {{nickcheck}}
    <div class="clearfix">
      <button class="cancelbtn">Cancel</button>
      <button class="signupbutton" @click="checkValid">아이디 생성</button>
    </div>
    
  </div>
{{ message }}

    </body>
  </main>
</template>

