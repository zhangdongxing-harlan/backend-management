<template>
    <div id="page-header" >
      <nav class="navbar navbar-default">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <router-link to="/" class='navbar-brand'>用户管理系统</router-link>
        </div>
        <div id="navbar" class="collapse navbar-collapse">
          <ul class="nav navbar-nav">
            <li><router-link to="/">主页</router-link></li>
            <li><router-link to="/about">关于</router-link></li>
          </ul>
          <ul class="nav navbar-nav navbar-right">
              <li><router-link to="/add">添加用户</router-link></li>
          </ul>
        </div><!--/.nav-collapse -->
      </div>
    </nav>       
    </div>
</template>
<script>
export default {
    
}
</script>
