<template>
    <div class="login">
        <h1>Đăng nhập</h1>
        <InputBase content="Username" type="text" placeholder="Enter your username" />
        <InputBase content="Password" type="password" placeholder="Enter your password" />
        <input type="button">
        <input type="checkbox" name="" id="">
    </div>
</template>
<script lang="ts" setup>
import InputBase from '../components/common/InputBase.vue';
</script>