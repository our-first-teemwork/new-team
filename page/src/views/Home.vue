<template>
  <div class="home" >
<headc/>
  <div class="body">

    <div class="title">
      <br><br>
      <h1>实验室管理系统</h1>
      <Divider orientation="center"/>
    </div>

     <div class="cards-wrapper">
      
        <Card style="width:320px">
          <Tabs  value="login">
            <TabPane label="登录" name="login" >
                <div class="box">
            <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" >
              <FormItem prop="choose">
                <Select v-model="formValidate.choose" placeholder="请选择登录身份" style="width:250px">
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
            </TabPane>

            <TabPane label="注册" name="register">
              <Form ref="formCustom" :model="formCustom" :rules="ruleCustom" >
                <FormItem prop="username">
                  <Input v-model="formCustom.username" prefix="ios-contact"  placeholder="请输入用户名" style="width:250px"/>
                </FormItem>
                <FormItem prop="password">
                  <Input v-model="formCustom.password" prefix="md-lock"  placeholder="请输入密码" style="width:250px"/>
                </FormItem>
                <FormItem prop="passwordCheck">
                  <Input v-model="formCustom.passwordCheck" prefix="md-lock"  placeholder="请重复密码" style="width:250px"/>
                </FormItem>
                <FormItem prop="phone">
                  <Input v-model="formCustom.phone" prefix="ios-call"  placeholder="请输入手机号" style="width:250px"/>
                </FormItem>
                <FormItem prop="number">
                  <Input v-model="formCustom.number" prefix="md-paper-plane"  placeholder="请输入学号/工号" style="width:250px"/>
                </FormItem>
                <FormItem prop="name">
                  <Input v-model="formCustom.name" prefix="md-happy"  placeholder="请输入姓名" style="width:250px"/>
                </FormItem>
                <FormItem>
                  <Button type="success" @click="handleSubmit('formCustom')" style="margin-bottom:5px;">注册</Button>
                </FormItem>
              </Form>
            </TabPane>

            </Tabs>
        </Card>
        
      
     </div>
</div>

    <div class="footer">
      <p>版权所有：xxxxxxxxxxxxxxx公司</p>
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
import headc from '@/components/headc.vue'
import cardlogin from '@/components/cardlogin.vue'

export default {
  name: 'home',
  components: {
   headc,cardlogin,
  },
  data () {
    const validatePass = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入密码'));
                } else {
                    if (this.formCustom.passwordCheck !== '') {
                        // 对第二个密码框单独验证
                        this.$refs.formCustom.validateField('passwdCheck');
                    }
                    callback();
                }
            };
            const validatePassCheck = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请再次输入您的密码！'));
                } else if (value !== this.formCustom.password) {
                    callback(new Error('重复密码不匹配！'));
                } else {
                    callback();
                }
            };
            return {
              formValidate:{
                choose:'',
                username: '',
                password: '',
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
              },
              formCustom:{
                username: '',
                password: '',
                passwordCheck: '',
                phone: '',
                number: '',
                name: '',
              },
              ruleCustom: {
                    username:[
                        { required: true, message: '用户名为空！', trigger: 'blur' }
                    ],
                    password: [
                        { validator: validatePass, trigger: 'blur' }
                    ],
                    passwordCheck: [
                        { validator: validatePassCheck, trigger: 'blur' }
                    ],
                    phone: [
                        { required: true, message: '联系方式为空！', trigger: 'blur' }
                    ],
                    number: [
                        { required: true, message: '学号/工号为空！', trigger: 'blur' }
                    ],
                    name: [
                        { required: true, message: '姓名为空！', trigger: 'blur' }
                    ],
                },
            }



        },
         methods: {
            handleSubmit (name) {
                this.$refs[name].validate((valid) => {
                    if (valid) {
                        this.$Message.success('Success!');
                        this.$router.push({name: 'login'});
                    } else {
                        this.$Message.error('Fail!');
                    }
                })
            }
        }
}
</script>

<style>



.body{
  background-image: url("../assets/pic.jpg");
  height: 720px;
  display: flex;
  flex-direction:column;
  justify-items: center;
  align-items: center;
}

.title{
  margin-top:48px; 
}
h1{
  font-size: 48px;
  color: white;
}

.ivu-tabs-nav-wrap {
    text-align: center;
}
.ivu-tabs-nav-scroll {
    display: inline-block;
}

.box{
  display: flex;
  flex-direction:column;
  justify-items: center;
  align-items: center;
}
Button{
    display:block; 
    width:250px; 
    height:35px; 
    line-height: 40px; 
    margin:0 auto; 
    border:none; 
    background-color:#2DB7F5; 
    color:#fff; 
    font-size:16px; 
    margin-bottom:5px;
  }
</style>