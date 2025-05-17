<template>
  <div class="main-container" v-if="isUserOrAdmin">
    <h1>
      您好，武汉纺织大学外经贸<br>
      <span >
        {{ user.role === 'ADMIN' ? '管理员' : '学生' }}
      </span>
      
      <span :style="{ color: '#002594' }">
        {{ user.name }}
      </span>, 欢迎您!
    </h1>
  </div>

  <!-- 如果既不是用户也不是管理员，就不显示-->
  <div class="main-container " v-else>
    <h1>您不是外经贸成员，请退出系统</h1>
  </div>
</template>

<script setup>
const user = JSON.parse(localStorage.getItem('student-user') || '{}');
const isUserOrAdmin = ['ADMIN', 'STUDENT'].includes(user.role);
</script>

<style>
.main-container {
  text-align: center;
}


</style>
