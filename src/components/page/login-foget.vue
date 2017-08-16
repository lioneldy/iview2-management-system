<style scoped>
</style>

<template>
<i-form class="register-form" action="/user/save" method="post">
    <h3>短信认证</h3>
        <p> 已有账号，请&nbsp;<a href="../index.html">登&nbsp;录</a></p>

    <div class="alert alert-danger display-hide">
        <button class="close" data-close="alert"></button>
        <span>信息有误，请核对！</span>
    </div>

    <div class="form-group">
        <label class="control-label visible-ie8 visible-ie9">手机号</label>
        <div class="input-icon">
            <i class="fa fa-phone"></i>
            <input class="form-control placeholder-no-fix" type="text" placeholder="请输入手机号" name="" /> </div>
    </div>


    <div class="form-group">
        <label class="control-label visible-ie8 visible-ie9">验证码</label>
        <div class="input-group input-icon">
            <i class="fa fa-shield"></i>
            <input class="form-control placeholder-no-fix" type="text" name="code" placeholder="验证码" style="border-top-left-radius: 4px; border-bottom-left-radius: 4px;" />
            <span class="input-group-btn">
                <button class="btn" type="button" name="getSmsCode" data-sms-type="0"> 获取验证码</button>
            </span>
        </div>

    <div style="clear: both;"></div>
    </div>
        <div class="form-group" style="margin-top: 10px;">
            <label style="float: right;">
            通过<a href="/login/securityQuestion">密码保护</a>找回密码
            </label>
        <div id="register_tnc_error"> </div>
    </div>

    <div class="form-actions">
        <button id="register-back-btn" type="button" class="btn red btn-outline"> 回登录页 </button>
        <button type="submit" id="register-submit-btn" class="btn green pull-right"> 下一步 </button>
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
                        message: '请填写用户名',
                        trigger: 'blur'
                    }],
                    password: [{
                        required: true,
                        message: '请填写密码',
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
                handleReset(val) {
                    console.log(val)
                }
        }
}

</script>
