<template>
  <div class="register">
    <h2>用户注册</h2>
    <form @submit.prevent="handleRegister">
      <div class="form-group">
        <label for="username">用户名：</label>
        <input type="text" v-model="username" required class="input-field" />
      </div>
      <div class="form-group">
        <label for="password">密码：</label>
        <input type="password" v-model="password" required class="input-field" />
      </div>
      <div class="button-group">
        <button type="submit" class="submit-button">注册</button>
      </div>
    </form>
  </div>
</template>

<script>
import { register } from "@/api/user";

export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async handleRegister() {
      try {
        const response = await register(this.username, this.password);
        if (response.code === 0) {
          alert("注册成功！");
          this.$router.push("/login");
        } else {
          alert("注册失败：" + response.message);
        }
      } catch (error) {
        alert("注册失败：" + error.message);
      }
    },
  },
};
</script>

<style scoped>
.register {
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
</style>