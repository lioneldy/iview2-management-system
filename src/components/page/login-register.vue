<style scoped>

</style>

<template>
<i-form class="register-form" action="/user/save" method="post">
        <h3>用户注册</h3>
        <p> 已有账号，请&nbsp;<a href="/login">登&nbsp;录</a></p>

        <div class="alert alert-danger display-hide">
            <Button class="close" data-close="alert"></Button>
            <span>信息有误，请核对！</span>
        </div>

        <div class="form-group">
            <label class="control-label visible-ie8 visible-ie9">用户名</label>
            <div class="input-icon">
                <i class="fa fa-user"></i>
                <Input class="form-control placeholder-no-fix" type="text" placeholder="请输入用户名" name="userId">
                </Input>
            </div>
        </div>

        <div class="form-group">
            <label class="control-label visible-ie8 visible-ie9">密码</label>
            <div class="input-icon">
                <i class="fa fa-lock"></i>
                <input class="form-control placeholder-no-fix" type="password" placeholder="密码8-16位数字和字母组合" name="password" id="password" />
            </div>
        </div>

        <div class="form-group">
            <label class="control-label visible-ie8 visible-ie9">密码确认</label>
            <div class="input-icon">
                <i class="fa fa-lock"></i>
                <input class="form-control placeholder-no-fix" type="password" autocomplete="off" placeholder="请重新输入密码" name="passwordConfirm" />
            </div>
        </div>

        <div class="form-group">
            <label class="control-label visible-ie8 visible-ie9">手机号</label>
            <div class="input-icon">
                <i class="fa fa-phone"></i>
                <input class="form-control placeholder-no-fix" type="text" placeholder="请输入手机号" name="tel" /> </div>
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
            <label class="mt-checkbox mt-checkbox-outline">
                <input type="checkbox" name="remember" value="1" />
                <input type="checkbox" name="tnc" />
                阅读并同意<a href="javascript:;">《北京新方通信技术有限公司网站服务协议》</a>及相关服务条款
                <span></span>
            </label>
            <div id="register_tnc_error"> </div>
        </div>
        <div class="form-actions">
            <button type="button" id="goBackToLogin" class="btn red btn-outline"> 回登录页 </button>
            <button type="submit" id="registerSubmitBtn" class="btn green pull-right"> 提交 </button>
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
