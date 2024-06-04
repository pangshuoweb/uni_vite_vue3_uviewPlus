<script setup>
import useStore from "@/store/modules"

const router = useRouter()
const { loginStore } = useStore()

/* 生命周期 */
const title = ref("登录页")
onLoad(() => {
   // loginReq()
})
const model1 = reactive({
   userInfo: {
      name: "",
      password: "",
   },
})
const rules = {
   "userInfo.name": [
      {
         required: true,
         message: "请输入姓名",
         trigger: ["blur", "change"],
      },
   ],
}

/* 登录请求 */
const loginReq = async () => {
   // const params = { userName: 1, password: 123 }
   // const res = await uni.$api.getExamNotice(params)
   // if (res.result) {
   //   uni.showToast({ title: "登录成功", icon: "success" })
   loginStore.setToken("abcdefg1234567")
   console.log(router)
   router.push("/pages/form/index")
   // router.pushTab("/pages/home/index")
   // } else {
   //   uni.$u.toast(res.message)
   // }
}
</script>

<template>
   <view class="content">
      <!-- <view class="text-area">
         <text class="title">{{ title }}</text>
      </view> -->
      <!-- <image class="logo" src="/static/logo.png"></image> -->
      <u--form labelPosition="left" class="form" :model="model1" :rules="rules" ref="uForm">
         <u-form-item label="账号" prop="userInfo.name" border ref="item1" labelAlign="left"
            :labelStyle="{ color: '#909399' }" labelWidth="'80'">
            <u--input v-model="model1.userInfo.name"></u--input>
         </u-form-item>
         <u-form-item label="密码" prop="userInfo.password" border ref="item1" labelAlign="left"
            :labelStyle="{ color: '#909399' }" labelWidth="'80'">
            <u--input v-model="model1.userInfo.name"></u--input>
         </u-form-item>
      </u--form>

      <u-button class="login-btn" type="primary" text="登录" @click="loginReq" />
   </view>
</template>

<style lang="scss">
.content {
   width: 100%;
   height: 100%;
   padding-top: 60rpx;
   display: flex;
   flex-direction: column;
   align-items: center;
   justify-content: center;
   margin-top: 20rpx;

   .form {
      width: 700rpx;
      margin: 20rpx 25rpx;
      padding: 20rpx;
      box-sizing: border-box;
      margin: 20rpx 25rpx;
   }

   .logo {
      height: 200rpx;
      width: 200rpx;
      margin-top: 200rpx;
      margin-left: auto;
      margin-right: auto;
      margin-bottom: 50rpx;
   }

   .text-area {
      display: flex;
      justify-content: center;
   }

   .title {
      font-size: 36rpx;
      color: #8f8f94;
   }

   .login-btn {
      // width: 200rpx;
      width: 660rpx;
      margin: 20rpx 45rpx;
   }
}
</style>
