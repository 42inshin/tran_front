<script setup lang="ts">
<<<<<<< HEAD
import router from '@/router';
import { useUserStore } from '@/stores/user';
import axios from 'axios';
import { onBeforeMount, ref } from 'vue';
import { useCookies } from 'vue3-cookies';
import QrcodeVue from 'qrcode.vue'
=======
import router from "@/router";
import { useUserStore } from "@/stores/user";
import axios from "axios";
import { onBeforeMount, ref } from "vue";
import { useCookies } from "vue3-cookies";
import QrcodeVue from "qrcode.vue";
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
export type UserType = {
  id: string;
  nickname: string;
  win: number;
  lose: number;
  admin: Boolean;
  avatarPath: string;
<<<<<<< HEAD
  twoFactorAuthenticationSecret: string,
  isTwoFactorAuthenticationEnabled: boolean,
  lating: number,
=======
  twoFactorAuthenticationSecret: string;
  isTwoFactorAuthenticationEnabled: boolean;
  lating: number;
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
};

let store = useUserStore();
let id_validate = ref(true);
let selectFile = ref();
let nickname = ref();
let leftval = ref("");
let twoFactor1 = ref(false);
let twoFactor11 = ref(true);
let qrValue = ref();
<<<<<<< HEAD
let qrCodeText=ref();
=======
let qrCodeText = ref();
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
let twoFactor2 = ref();
let backval = ref();
const { cookies } = useCookies();
let user = ref();

onBeforeMount(async () => {
<<<<<<< HEAD
  await axios.get("/api/users", {
        headers: {
          Authorization: `Bearer ` + cookies.get('jwt'),
        },
      })
    .then(res => {
      user.value = res.data;
      user.value.avatarPath = "http://localhost:5000/" + res.data.avatarPath;
      console.log(user.value);
      if (user.value.isTwoFactorAuthenticationEnabled)
      {
        leftval.value = "40px";
        backval.value = '#53FF4C';
=======
  await axios
    .get("/api/users", {
      headers: {
        Authorization: `Bearer ` + cookies.get("jwt"),
      },
    })
    .then((res) => {
      user.value = res.data;
      user.value.avatarPath = "http://localhost:5000/" + res.data.avatarPath;
      console.log(user.value);
      if (user.value.isTwoFactorAuthenticationEnabled) {
        leftval.value = "40px";
        backval.value = "#53FF4C";
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
        twoFactor2.value = true;
        twoFactor1.value = true;
        twoFactor11.value = false;
      }
      nickname.value = res.data.nickname;
    })
<<<<<<< HEAD
=======
<<<<<<<< HEAD:front/src/views/Info.vue
    .catch((error) => {
      console.log(error);
      console.log(`api GET /users error`);
    });
});
========
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
    .catch(error => {
        console.log(error);
        console.log(`api GET /users error`);
    })

})
<<<<<<< HEAD
=======
>>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf:ft_front/src/views/Info.vue
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf

/* png??? ????????? QRcode uri src ??????????????? ?????????????????? ??????????????? ??????
function _arrayBufferToBase64( buffer : any) {
    var binary = '';
    var bytes = new Uint8Array( buffer );
    var len = bytes.byteLength;
    for (var i = 0; i < len; i++) {
        binary += String.fromCharCode( bytes[ i ] );
    }
    return window.btoa( binary );
}
*/

async function updateUserData() {
  console.log(nickname);
<<<<<<< HEAD
  await axios.post("/api/users/nickname/", { nickname: nickname.value },
    {
      headers: {
        Authorization: `Bearer ` + cookies.get('jwt'),
      }
    }
  )
=======
  await axios
    .post(
      "/api/users/nickname/",
      { nickname: nickname.value },
      {
        headers: {
          Authorization: `Bearer ` + cookies.get("jwt"),
        },
      }
    )
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
    .then((res) => {
      console.log(res);
      console.log("send updateUserData Succcess");
      user.value.nickname = nickname.value;
    })
    .catch((error) => {
      console.log(error);
<<<<<<< HEAD
      if (error.response.data.statusCode == 409)
        id_validate.value = false;
      else
        router.push('/');
    })
=======
      if (error.response.data.statusCode == 409) id_validate.value = false;
      else router.push("/");
    });
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
}

async function updateAvatar() {
  if (selectFile.value.files[0]) {
    // Form ?????? ??????
    let form = new FormData();
    console.log(selectFile.value.files[0]);
<<<<<<< HEAD
    form.append("file", selectFile.value.files[0]) // api file name

    await axios.post("/api/users/avatar", form, {
        headers: {
          "Content-Type": "multipart/form-data",
          Authorization: `Bearer ` + cookies.get('jwt'),
        },
      })
    .then(res => {
        store.data.avatarPath = "about:blank";
        setTimeout(() => { store.data.avatarPath = "http://localhost:5000/" + res.data }, 0)
        console.log("ok");
    })
    .catch(error => {
        console.log(error);
        console.log("nk");
=======
    form.append("file", selectFile.value.files[0]); // api file name

    await axios
      .post("/api/users/avatar", form, {
        headers: {
          "Content-Type": "multipart/form-data",
          Authorization: `Bearer ` + cookies.get("jwt"),
        },
      })
      .then((res) => {
        store.data.avatarPath = "about:blank";
<<<<<<<< HEAD:front/src/views/Info.vue
        setTimeout(() => {
          store.data.avatarPath = "http://localhost:5000/" + res.data;
        }, 0);
========
        setTimeout(() => { store.data.avatarPath = "http://localhost:5000/" + res.data }, 0)
>>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf:ft_front/src/views/Info.vue
        console.log("ok");
      })
      .catch((error) => {
        console.log(error);
        console.log("nk");
<<<<<<<< HEAD:front/src/views/Info.vue
      });
  } else {
    alert("????????? ????????? ?????????.");
========
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
    })
  }
  else {
    alert("????????? ????????? ?????????.")
<<<<<<< HEAD
  }
}


async function twoFAClick() {
  console.log(`twoFactorValue = ${twoFactor1.value}`);
  if (!twoFactor1.value) {
    axios.get("/api/users/generate", {
        headers: {
          Authorization: `Bearer ` + cookies.get('jwt'),
        },
      })
    .then(res => {
      qrValue.value = res.data;
      twoFactor1.value = true;
    })
    .catch(error => {
        console.log(error);
        console.log(`api /users/generate error`);
    })
  }
  else {
    leftval.value = "0px";
    backval.value = '#CCCCCC';
    twoFactor1.value = false;
    twoFactor2.value = false;
    axios.post("/api/users/turn-off", { code: qrCodeText.value}, {
        headers: {
          Authorization: `Bearer ` + cookies.get('jwt'),
        },
      })
=======
>>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf:ft_front/src/views/Info.vue
  }
}

async function twoFAClick() {
  console.log(`twoFactorValue = ${twoFactor1.value}`);
  if (!twoFactor1.value) {
    axios
      .get("/api/users/generate", {
        headers: {
          Authorization: `Bearer ` + cookies.get("jwt"),
        },
      })
      .then((res) => {
        qrValue.value = res.data;
        twoFactor1.value = true;
      })
      .catch((error) => {
        console.log(error);
        console.log(`api /users/generate error`);
      });
  } else {
    leftval.value = "0px";
    backval.value = "#CCCCCC";
    twoFactor1.value = false;
    twoFactor2.value = false;
    axios.post(
      "/api/users/turn-off",
      { code: qrCodeText.value },
      {
        headers: {
          Authorization: `Bearer ` + cookies.get("jwt"),
        },
      }
    );
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
  }
}

async function twoFactorAuthentication() {
  console.log(`two authen`);
  console.log(localStorage.getItem("accesstoken"));
<<<<<<< HEAD
  axios.post("/api/users/turn-on", { code: qrCodeText.value}, {
        headers: {
          Authorization: `Bearer ` + cookies.get('jwt'),
        },
      })
    .then(res => {
      leftval.value = "40px";
      backval.value = '#53FF4C';
      twoFactor2.value = true;
      twoFactor1.value = false;

    })
    .catch(error => {
        console.log(`api /users/turn-on error`);
    })
}

</script>

<template>
  <div class="box" style="background: #BDBDBD;">
    <img class="profile" :src="store.data.avatarPath">
=======
  axios
    .post(
      "/api/users/turn-on",
      { code: qrCodeText.value },
      {
        headers: {
          Authorization: `Bearer ` + cookies.get("jwt"),
        },
      }
    )
    .then((res) => {
      leftval.value = "40px";
      backval.value = "#53FF4C";
      twoFactor2.value = true;
      twoFactor1.value = false;
    })
    .catch((error) => {
      console.log(`api /users/turn-on error`);
    });
}
</script>

<template>
  <div class="box" style="background: #bdbdbd">
    <img class="profile" :src="store.data.avatarPath" />
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
  </div>
  <h2 class="title">???????????? ??????</h2>
  <table class="userDataTable">
    <colgroup>
<<<<<<< HEAD
      <col style="width: 180px;">
      <col>
=======
      <col style="width: 180px" />
      <col />
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
    </colgroup>
    <tbody>
      <tr>
        <!-- ????????? ??? ?????? -->
<<<<<<< HEAD
        <th class="row"> ????????? </th>
        <input type="text" v-model="nickname">
      </tr><!-- ????????? ??? ??? -->
      <tr>
        <th class="row"> ??? </th>
        <td> {{ store.data.win }} </td>
      </tr>
      <tr>
        <th class="row"> ??? </th>
        <td> {{ store.data.lose }} </td>
      </tr>
      <tr>
        <th class="row"> ????????? </th>
        <td>
          <form @submit.prevent="updateAvatar" method="post">
            <input type="file" ref="selectFile"/>
=======
        <th class="row">?????????</th>
        <input type="text" v-model="nickname" />
      </tr>
      <!-- ????????? ??? ??? -->
      <tr>
        <th class="row">???</th>
        <td>{{ store.data.win }}</td>
      </tr>
      <tr>
        <th class="row">???</th>
        <td>{{ store.data.lose }}</td>
      </tr>
      <tr>
        <th class="row">?????????</th>
        <td>
          <form @submit.prevent="updateAvatar" method="post">
            <input type="file" ref="selectFile" />
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
            <button type="submit">????????? ??????</button>
          </form>
        </td>
      </tr>
      <tr>
<<<<<<< HEAD
        <th class="row"> 2?????? ?????? </th>
        <td>
          <div class='toggleBG' v-bind:style="{background: backval}" @click="twoFAClick">
            <button class='toggleFG' v-bind:style="{left: leftval}"></button>
          </div>
          <div v-if="twoFactor2"> ????????? ????????????????????? </div>
        </td>

      </tr>
      <tr v-if="twoFactor1 && twoFactor11">
        <th class="row"> <qrcode-vue :value="qrValue"></qrcode-vue></th>
          <!-- ??????..??????..<img :src="'data:image/jpeg;base64,'+qrValue"/></th>-->
        <td>
          <input type="text" v-model="qrCodeText"/>
          <input type="button" value="??????" @click="twoFactorAuthentication"/>
        </td>
      </tr>
    </tbody>

  </table>
  <div v-if="!id_validate">?????? ???????????? ????????? ?????????.</div>
  <input type="button" @click="updateUserData" value="??????">
</template>


=======
        <th class="row">2?????? ??????</th>
        <td>
          <div class="toggleBG" v-bind:style="{ background: backval }" @click="twoFAClick">
            <button class="toggleFG" v-bind:style="{ left: leftval }"></button>
          </div>
          <div v-if="twoFactor2">????????? ?????????????????????</div>
        </td>
      </tr>
      <tr v-if="twoFactor1 && twoFactor11">
        <th class="row"><qrcode-vue :value="qrValue"></qrcode-vue></th>
        <!-- ??????..??????..<img :src="'data:image/jpeg;base64,'+qrValue"/></th>-->
        <td>
<<<<<<<< HEAD:front/src/views/Info.vue
          <input type="text" v-model="qrCodeText" />
          <input type="button" value="??????" @click="twoFactorAuthentication" />
========
          <input type="text" v-model="qrCodeText"/>
          <input type="button" value="??????" @click="twoFactorAuthentication"/>
>>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf:ft_front/src/views/Info.vue
        </td>
      </tr>
    </tbody>
  </table>
  <div v-if="!id_validate">?????? ???????????? ????????? ?????????.</div>
  <input type="button" @click="updateUserData" value="??????" />
</template>

>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
<style scoped>
.input_text {
  -webkit-text-size-adjust: none;
  --animate-duration: 1s;
  --animate-delay: 1s;
  --animate-repeat: 1;
  --swiper-theme-color: #007aff;
  --main-color: #152348;
  --main-light-color: #e5edf8;
  border-spacing: 0;
  border-collapse: collapse;
  word-break: break-all;
  font-family: Noto Sans KR, sans-serif;
  vertical-align: middle;
  box-sizing: border-box;
  -webkit-appearance: none;
  width: 300px !important;
  font-size: 16px;
  background: transparent;
  padding: 0 17px;
  height: 40px;
  border: 1px solid #d0d3da;
  border-radius: 8px;
}

.row {
  -webkit-text-size-adjust: none;
  --animate-duration: 1s;
  --animate-delay: 1s;
  --animate-repeat: 1;
  --swiper-theme-color: #007aff;
  line-height: 24px;
<<<<<<< HEAD
  letter-spacing: -.5px;
=======
  letter-spacing: -0.5px;
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
  --main-color: #152348;
  --main-light-color: #e5edf8;
  font-family: Noto Sans KR, sans-serif;
  border-spacing: 0;
  border-collapse: collapse;
  font-size: 15px;
  margin: 0;
  box-sizing: border-box;
  border-bottom: 1px solid #dedede;
  padding: 15px 10px;
  height: 58px;
  color: #555;
  font-weight: 500;
  vertical-align: top;
  background: #fff;
}

.userDataTable {
  -webkit-text-size-adjust: none;
  --animate-duration: 1s;
  --animate-delay: 1s;
  --animate-repeat: 1;
  --swiper-theme-color: #007aff;
  text-align: left;
  color: #222;
  line-height: 24px;
<<<<<<< HEAD
  letter-spacing: -.5px;
=======
  letter-spacing: -0.5px;
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
  --main-color: #152348;
  --main-light-color: #e5edf8;
  margin: 0;
  padding: 0;
  font-family: Noto Sans KR, sans-serif;
  box-sizing: border-box;
  width: 100%;
  font-weight: 400;
  border-spacing: 0;
  border-collapse: collapse;
  margin-bottom: 80px !important;
  font-size: 15px;
  border-top: 1px solid #dedede;
}

.buttons {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}
.box {
<<<<<<< HEAD
=======
<<<<<<<< HEAD:front/src/views/Info.vue
  width: 150px;
  height: 150px;
  border-radius: 70%;
  overflow: hidden;
========
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
    width: 150px;
    height: 150px;
    border-radius: 70%;
    overflow: hidden;
<<<<<<< HEAD
}
.profile {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.toggleBG {
  background:#CCCCCC;
  width:70px;
  height:30px;
  border:1px solid#CCCCCC;
  border-radius:15px;
}
.toggleFG {
  background:#161111;
  width:30px;
  height:30px;
  border:none;
  border-radius:15px;
  position:relative;
  left:0px;
}

=======
>>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf:ft_front/src/views/Info.vue
}
.profile {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.toggleBG {
  background: #cccccc;
  width: 70px;
  height: 30px;
  border: 1px solid#CCCCCC;
  border-radius: 15px;
}
.toggleFG {
  background: #161111;
  width: 30px;
  height: 30px;
  border: none;
  border-radius: 15px;
  position: relative;
  left: 0px;
}
>>>>>>> 3766c3bdeed1cef82e76f9d4476747ce45bbb1bf
</style>
