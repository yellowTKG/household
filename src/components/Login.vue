<template>
    <div class="Login-container">
        <!-- 
            左側コンテンツ
            id, password 入力欄とログインボタン 
        -->
        <div class="Login-left">
            <div class="left-contents">
                <div class="title-field">
                    <h1>
                        Login
                    </h1>
                </div>
                <div class="input-field">
                    <InputField
                        msg="input your userid"
                        id="userid"
                        placeholder="ex) userid1"
                        :value="id" 
                        @inputedEvent="handleInputedEvent"    
                    ></InputField>
                    <InputField
                        msg="input your password"
                        id="password"
                        placeholder="ex) aaaa1111"
                        :value="password"  
                        @inputedEvent="handleInputedEvent"   
                    ></InputField>
                </div>
                <div class="btn-field">
                    <button @click="login">Login</button>
                </div>
            </div>
        </div>
        <!-- 
            右側コンテンツ
            スタイリッシュな画像など
         -->
        <div class="login-right">
            <h1>
                Login
            </h1>
        </div>
    </div>
</template>

<script setup>
// インポート
import InputField from './parts/InputField.vue'

// // API を叩く関数（GET）
// async function getData(url = "", data = {}) {
//   // 既定のオプションには * が付いています
//   const response = await fetch(url, {
//     method: "GET",
//     mode: "cors", // no-cors, *cors, same-origin
//     cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
//     credentials: "same-origin",
//     headers: {
//       "Content-Type": "application/json",
//     },
//     redirect: "follow",
//     referrerPolicy: "no-referrer",
//   });
//   return response.json(); // JSON のレスポンスをネイティブの JavaScript オブジェクトに解釈
// }

const sendData = {
    "userid":"",
    "password":""
}

// 子からデータを受け取り、ログインボタンで送信するデータに格納
const handleInputedEvent = (argFromChild) => {
    if (argFromChild.key === 'userid') {
        sendData['userid'] = argFromChild.value
    } else {
        sendData['password'] = argFromChild.value
    }
}


// ログインボタンの処理
// const baseURL = "https://bagq420mb9.execute-api.ap-southeast-2.amazonaws.com/prod/login"
const login = () => {
    console.log("login")
    console.log(sendData)
    // getData(
    //     baseURL + "?" 
    //     + "userid=" + sendData.userid
    //     + "&"
    //     + "password" + sendData.password  
    //     )
    //     .then((response) => {
    //     console.log(response); // `response.json()` の呼び出しで解釈された JSON データ
    // });
}

</script>

<style scoped>
.Login-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

.Login-left {
    width: 50vw;
    height: 100vh;
    display: grid;
    justify-items: center; /* X axis*/
    align-items: center; /* Y axis*/
}

.login-right {
    width: 50vw;
    height: 100vh;
    background: rgb(163, 163, 82);
}

.left-contents {
    width: 80%;
    /* margin: 0 auto; */
    text-align: center;
}

</style>



