<template>
  <div class="cardlogin">
      <div class="box">
            <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" >
              <FormItem prop="choose">
                <Select v-model="formValidate.choose" placeholder="请选择登录身份" style="width:250px;height=330px;">
                <!--  <Option v-for="item in cityList" :value="item.value" :key="item.value" >{{ item.label }}</Option>  -->
                <Option value="user">用户</Option>
                <Option value="admin">管理员</Option>
              </Select>
              </FormItem>
              <FormItem prop="username">
                <Input v-model="formValidate.username" prefix="ios-contact" size="large" placeholder="请输入工号/用户名" style="width:250px,margin:10px;"/>
              </FormItem>
              <FormItem  prop="password">
                <Input v-model="formValidate.password" prefix="md-lock" size="large" type="password" placeholder="请输入密码" style="width:250px,margin:10px; "/>
              </FormItem>
              <FormItem>
                <Button type="info" @click="handleSubmit('formValidate')" style="margin-bottom:5px;">登录</Button>
              </FormItem>
        <!--    <p v-show="showTishi">{{tishi2}}</p>  -->
          </Form>
        </div>


  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'cardlogin',
  data () {
        
            return {
              formValidate:{
              showLogin: true,
              showRegister: false,
              showTishi: false,
              tishi1: '',
              tishi2:'',
              username: '',
              password: '',
              phone:'',
              value:'',
           /*     cityList: [
                    {
                        value: 'user',
                        label: '用户'
                    },
                    {
                        value: 'admin',
                        label: '管理员'
                    },
                ],
                model: ''
              */
              },
              ruleValidate:{
                choose:[
                  { required: true, message: '请选择登录身份！', trigger: 'change' }
                ],
                username:[
                  { required: true, message: '用户名/工号为空！', trigger: 'blur' }
                ],
                password:[
                  { required: true, message: '密码为空！', trigger: 'blur' },
                ]
              }
            }
        },
         methods: {
            handleSubmit (name) {
                this.$refs[name].validate((valid) => {
                    if (valid) {
                        this.$Message.success('Success!');
                    } else {
                        this.$Message.error('Fail!');
                    }
                })
            }
        }
}
</script>

<style>
.box{
  display: flex;
  flex-direction:column;
  justify-items: center;
  align-items: center;
}
</style>
