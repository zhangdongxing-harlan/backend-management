<template>
    <div id="customer" class='container'>
        <h2 class='page-header'>用户管理系统</h2>
        <alert :mes="mes" v-if="mes"></alert>
        <input type="text" class="form-control" placeholder="搜索" v-model="filterName"> 
        <table class="table table-striped">
            <thead>
                <tr>
                    <th>姓名</th>
                    <th>电话</th>
                    <th>邮箱</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for='item in filterData' :key="item.id">
                    <th>{{item.name}}</th>
                    <th>{{item.phone}}</th>
                    <th>{{item.email}}</th>
                    <th><router-link :to="'/customer/'+item.objectId" class="btn btn-default">详情</router-link></th>
                </tr>
            </tbody>
        </table>

    </div>
</template>
<script>
import Alert from './Alert'
import Bmob from "hydrogen-js-sdk"
Bmob.initialize("a2d4e5085b301996b25a43c1fe5b47b5", "010535e63b33f7a56c1e466ef69fe09a");
export default {
    name:'customer',
    data(){
        return {
            customer:[],
            mes:'',
            filterName:''
        }
    },
    methods:{
        getData(){
            const query = Bmob.Query('management_users');
            query.find().then(res=>{
                this.customer=res;
            });
        }
    },
    computed:{
        filterData(){
            return this.customer.filter(customer=>{
                return customer.name.match(this.filterName);
            })
        }
    },
    created(){
        if(this.$route.query.alert){
            this.mes = this.$route.query.alert;
        }
        this.getData();
    },
    components:{
        Alert
    }
}
</script>
