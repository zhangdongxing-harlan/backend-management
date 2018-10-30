<template>
    <div id="customer-details" class="details container">
        <router-link to="/" class="btn btn-default">返回</router-link>
        <h2 class="page-header">{{customer.name}}
            <span class="pull-right">
                <router-link :to="'/edit/'+customer.objectId" class="btn btn-primary">编辑</router-link> 
                <button class="btn btn-danger" @click="deleteCustomer(customer.objectId)">删除</button>
            </span>

        </h2>
        <ul class="list-group">
            <li class="list-group-item"><span class="glyphicon glyphicon-earphone"> {{customer.phone}}</span></li>
            <li class="list-group-item"><span class="glyphicon glyphicon-envelope"> {{customer.email}}</span></li>
        </ul>
        <ul class="list-group">
            <li class="list-group-item"><span class="glyphicon glyphicon-asterisk"> {{customer.education}}</span></li>
            <li class="list-group-item"><span class="glyphicon glyphicon-asterisk"> {{customer.graduationschool}}</span></li>
            <li class="list-group-item"><span class="glyphicon glyphicon-asterisk"> {{customer.profession}}</span></li>
            <li class="list-group-item"><span class="glyphicon glyphicon-asterisk"> {{customer.profile}}</span></li>
        </ul>
    </div>
</template>
<script>
export default {
  name: "customer-deatils",
  data() {
    return {
      customer: ""
    };
  },
  methods: {
    getData(id) {
      const query = Bmob.Query("management_users");
      query.get(id).then(res => {
        this.customer = res;
      });
    },
    deleteCustomer(id){
        const query = Bmob.Query("management_users");
        query.destroy(id).then(res=>{
            this.$router.push({path:'/',query:{alert:'删除成功'}})
        })
    }
  },
  created() {
    let id = this.$route.params.id;
    this.getData(id);
  }
};
</script>
<style>
 h2 .btn-primary {
     margin-right: 5px;
 } 
</style>
