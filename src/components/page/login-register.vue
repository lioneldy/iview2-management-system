<style scoped>
h1, p {
  color: #eee; 
}
</style>

<template>
<i-form ref="formInline" :model="formInline" :rules="ruleInline">
    <Form-item>
        <h1>用户注册</h1>
    </Form-item>
    <p> 已有账号，请<router-link to="login">登录</router-link></p>
    
    <Form-item prop="user">
        <Input v-model="formInline.user" placeholder="请输入用户名称">
            <Icon type="person" slot="prepend"></Icon>
        </Input>
    </Form-item>

    <Form-item prop="password">
        <Input v-model="formInline.password" placeholder="密码8-16位数字和字母组合">
            <Icon type="locked" slot="prepend"></Icon>
        </Input>
    </Form-item>

    <Form-item prop="passwordConfirm">
        <Input v-model="formInline.passwordConfirm" placeholder="请重新输入密码">
            <Icon type="locked" slot="prepend"></Icon>
        </Input>
    </Form-item>

    <Form-item prop="tel">
        <Input v-model="formInline.tel" placeholder="请输入手机号">
            <Icon type="android-call" slot="prepend"></Icon>
        </Input> 
    </Form-item>

    <Form-item prop="code">
        <Input v-model="formInline.code" placeholder="验证码">
            <Icon type="compose" slot="prepend"></Icon>
            <span slot="append">获取验证码</span>
        </Input>
    </Form-item>

    <Form-item>
        <Checkbox>阅读并同意<a href="javascript:;">《北京新方通信技术有限公司网站服务协议》</a>及相关服务条款</Checkbox>
    </Form-item>

    <Form-item>
        <Button type="primary" style="float:left;"> 回登录页 </Button>
        <Button type="primary" style="float:right;"> 提交 </Button>
    </Form-item>
</i-form>

</template>

<script>

export default {
    data() {
            return {
                formInline: {
                    user: '',
                    password: '',
                    passwordConfirm: '',
                    tel: '',
                    code: '',
                },
                ruleInline: {
                    user: [{
                        required: true,
                        message: '请输入用户名',
                        trigger: 'blur'
                    }],
                    password: [{
                        required: true,
                        message: '密码8-16位数字和字母组合',
                        trigger: 'blur'
                    }, {
                        type: 'string',
                        min: 6,
                        message: '密码长度不能小于6位',
                        trigger: 'blur'
                    }],
                    passwordConfirm:[{
                        required: true,
                        message: '密码8-16位数字和字母组合',
                        trigger: 'blur'
                    }],
                    tel: [{
                        required: true,
                        message: '请输入手机号',
                        trigger: 'blur'
                    }],
                    code: [{
                        required: true,
                        message: '请输入验证码',
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
                handleReset(val) {
                    console.log(val)
                }
        }
}

</script>
