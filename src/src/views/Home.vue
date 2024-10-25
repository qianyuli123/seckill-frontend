<template>
  <div class="home">
    <header class="header">
      <h1>欢迎来到在线秒杀系统</h1>
    </header>
    <nav class="nav">
      <router-link to="/register" class="nav-link">注册</router-link>
      <span class="separator">|</span>
      <router-link to="/login" class="nav-link">登录</router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>

<style scoped>
.header {
  text-align: center;
  background-color: #333;
  color: white;
  padding: 20px;
}

.nav {
  text-align: center;
  margin-top: 20px;
}

.nav-link {
  text-decoration: none;
  color: blue;
  padding: 5px 10px;
  border: 1px solid blue;
  border-radius: 5px;
  margin: 0 5px;
}

.separator {
  margin: 0 10px;
}

.separator {
  margin: 0 10px;
}
</style>