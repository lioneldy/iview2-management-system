<style scoped>
h1 {
  color: #eee; 
}
</style>

<template>
<i-form ref="formInline" :model="formInline" :rules="ruleInline">
    <Form-item>
        <h1 class="form-title">账户登录</h1>
    </Form-item>
    <Form-item prop="user">
        <Input v-model="formInline.user" placeholder="请输入用户名称">
            <Icon type="ios-person-outline" slot="prepend"></Icon>
        </Input>
    </Form-item>
    <Form-item prop="password">
        <Input v-model="formInline.password" placeholder="请输入密码">
            <Icon type="ios-locked-outline" slot="prepend"></Icon>
        </Input>
    </Form-item>
    <Form-item style = "text-align:right">
        <i-button type="primary" @click.native="handleSubmit('formInline')">登录</i-button>
    </Form-item>
    <hr>
    <div class="create-account" style="height: 40px;">
        <router-link to="register" style="float: left;">注册账号 </router-link>
        <router-link to="foget" style="float: right;">找回密码 </router-link>
    </div>
</i-form>


</template>

<script>

export default {
    data() {
        return {
            formInline: {
                user: '',
                password: '',
            },
            ruleInline: {
                user: [{
                    required: true,
                    message: '请输入用户名称',
                    trigger: 'blur'
                }],
                password: [{
                    required: true,
                    message: '请输入密码',
                    trigger: 'blur'
                }, {
                    type: 'string',
                    min: 6,
                    message: '密码长度不能小于6位',
                    trigger: 'blur'
                }]
            }
        }
    },
    methods: {
        handleSubmit(name) {
            this.$refs[name].validate((valid) => {
                if (valid) {
                    this.$Message.success('提交成功!');
                    this.$router.push('/about');
                } else {
                    this.$Message.error('表单验证失败!');
                }
            })
        },
    }
}

</script>
