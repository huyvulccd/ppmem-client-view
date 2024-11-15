<template>
    <div class="login">
        <h1>Đăng nhập</h1>
        <InputText placeholder="Mã nhân viên" v-model="username" />
        <InputText placeholder="Mật khẩu" type="password" v-model="password" />
        <ButtonCommon color="primary" size="large" id="submit">Đăng nhập</ButtonCommon>
        <div>
            <CheckboxComponent v-model="agreeToTerms" label="I agree to the terms and conditions" />
            <!-- <span><a href="/forgot">Quên mật khẩu?</a></span> -->
        </div>
    </div>
</template>
<script lang="ts" setup>
import { ref } from 'vue'
import InputText from '../components/common/input/InputText.vue';
import ButtonCommon from '@/components/common/input/ButtonCommon.vue';


const username = ref('')
const password = ref('')
const agreeToTerms = ref(false)
</script>

<style scoped>
.login {
    display: flex;
    gap: 10px;
    flex-direction: column;
    align-items: center;
}
</style>