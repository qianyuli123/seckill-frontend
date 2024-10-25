<template>
  <div class="login">
    <h2>用户登录</h2>
    <form @submit.prevent="handleLogin">
      <div class="form-group">
        <label for="username">用户名：</label>
        <input type="text" v-model="username" required class="input-field" />
      </div>
      <div class="form-group">
        <label for="password">密码：</label>
        <input type="password" v-model="password" required class="input-field" />
      </div>
      <div class="button-group">
        <button type="submit" class="submit-button">登录</button>
      </div>
    </form>
  </div>
</template>

<script>
import { login } from "@/api/user";

export default {
  data() {
    return {
      username: "",
      password: "",
      // 可以添加更多状态相关的数据，如登录错误提示信息
      errorMessage: ""
    };
  },
  methods: {
    async handleLogin() {
      try {
        const response = await login(this.username, this.password);
        if (response.code === 0) {
          alert("登录成功！");
          // 保存用户信息，跳转到首页
          localStorage.setItem("user", JSON.stringify(response.data));
          this.$router.push("/");
        } else {
          // 设置错误提示信息
          this.errorMessage = response.message;
          alert("登录失败：" + response.message);
        }
      } catch (error) {
        // 设置错误提示信息
        this.errorMessage = error.message;
        alert("登录失败：" + error.message);
      }
    },
  },
};
</script>

<style scoped>
.login {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #f4f4f4;
}

.form-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

.label {
  margin-bottom: 5px;
}

.input-field {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.button-group {
  display: flex;
  justify-content: center;
}

.submit-button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background-color: #007BFF;
  color: white;
  cursor: pointer;
}

.error-message {
  color: red;
  margin-top: 5px;
}
</style>