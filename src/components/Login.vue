<template>
  <div class="login">
    <div class="login-image">
      <van-image
        round
        fit="cover"
        width="10rem"
        height="10rem"
        src="https://img01.yzcdn.cn/vant/cat.jpeg"
      />
    </div>
    <div class="login-input">
      <van-form validate-first @failed="onFailed">
        <!-- 通过 pattern 进行正则校验 -->
        <van-field
          v-model="value1"
          name="pattern"
          label="账号"
          label-width="50"
          placeholder="账号"
          colon
          :rules="[{ pattern, message: '请输入正确内容' }]"
        />
        <!-- 通过 validator 进行函数校验 -->
        <van-field
          v-model="value2"
          name="validator"
          label="密码"
          label-width="50"
          placeholder="密码"
          colon
          :rules="[{ validator, message: '请输入正确内容' }]"
        />
        <!-- 通过 validator 进行异步函数校验 -->
        <!-- <van-field
          v-model="value3"
          name="asyncValidator"
          placeholder="异步函数校验"
          :rules="[{ validator: asyncValidator, message: '请输入正确内容' }]"
        /> -->
        <div class="login-button">
          <van-button round block type="info" class="login-submit" native-type="submit" @click="onSubmit"
            >提交</van-button>
            <van-button round block type="primary" native-type="submit" @click="onReg"
            >注册</van-button>
          
        </div>
      </van-form>
    </div>
  </div>
</template>

<script>
import { Toast } from 'vant';
export default {
  data() {
    return {
      value1: '',
      value2: '',
      pattern: /\d{6}/,
    }
  },
  methods: {
    // 校验函数返回 true 表示校验通过，false 表示不通过
    validator(val) {
      return /1\d{10}/.test(val);
    },
    // 异步校验函数返回 Promise
    // asyncValidator(val) {
    //   return new Promise((resolve) => {
    //     Toast.loading('验证中...');

    //     setTimeout(() => {
    //       Toast.clear();
    //       resolve(/\d{6}/.test(val));
    //     }, 1000);
    //   });
    // },
    onFailed(errorInfo) {
      console.log('failed', errorInfo);
    },
    onSubmit() {
      Toast.loading('验证中...');
    },
    onReg() {
      Toast.loading('注册')
    }
  },
  
};
</script>

<style scoped>
.login-image {
  margin-top: 50px;
}
.login-input {
  margin-top: 50px;
  padding: 0 20px;
}
.login-button {
  margin-top: 50px;
}
.login-submit {
  margin-bottom: 20px;
}
</style>