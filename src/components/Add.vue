<template>
    <div id="add" class="container">
        <h2 class="page-header">添加用户</h2>
        <form @submit="addCustomer">
            <div class="well">
                <h4>用户信息</h4>
                <div class="form-group">
                    <label>姓名</label>
                    <input type="text" class="form-control" placeholder="姓名" v-model="customer.name" required>
                </div>
                <div class="form-group">
                    <label>电话</label>
                    <input type="text" class="form-control" placeholder="电话" v-model="customer.phone" required>
                </div>
                <div class="form-group">
                    <label>邮箱</label>
                    <input type="text" class="form-control" placeholder="邮箱" v-model="customer.email" required>
                </div>
                <div class="form-group">
                    <label>学历</label>
                    <input type="text" class="form-control" placeholder="学历" v-model="customer.education">
                </div>
                <div class="form-group">
                    <label>毕业学校</label>
                    <input type="text" class="form-control" placeholder="毕业学校" v-model="customer.graduationschool">
                </div>
                <div class="form-group">
                    <label>职业</label>
                    <input type="text" class="form-control" placeholder="职业" v-model="customer.profession">
                </div>
                <div class="form-group">
                    <label>个人简介</label>
                    <textarea rows="10"  class="form-control" placeholder="个人简介" v-model="customer.profile"></textarea>
                </div>
                <button type="sumbit" class="btn btn-primary">提交</button>
            </div>
            
        </form>
    </div>
</template>
<script>
import Bmob from "hydrogen-js-sdk"
Bmob.initialize("a2d4e5085b301996b25a43c1fe5b47b5", "010535e63b33f7a56c1e466ef69fe09a");
export default {
  name: "add",
  data() {
    return {
      customer: {
          name:'',
          phone:'',
          email:'',
          education:'',
          graduationschool:'',
          profession:'',
          profile:''
      }
    };
  },
  methods:{
      addCustomer(e){
          e.preventDefault();
          const query = Bmob.Query('management_users');
          query.set('name',this.customer.name);
          query.set('phone',this.customer.phone);
          query.set('email',this.customer.email);
          query.set('education',this.customer.education);
          query.set('graduationschool',this.customer.graduationschool);
          query.set('profession',this.customer.profession);
          query.set('profile',this.customer.profile);
          query.save().then(res=>{
             this.$router.push({path:'/',query:{alert:'用户信息添加成功'}});
          })
      }
  }
};
</script>

