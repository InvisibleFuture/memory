<template>
  <div id="app">
    <header>
      <nav>
        <ul class="nav">
          <!-- 同类型 相合并到主页展示 故顶部无需 nav 条 -->
          <li v-for="item in navs"><router-link :to="item.url">{{ item.name }}</router-link></li>
        </ul>
        <!-- 此处判断角色登录状态 快捷键 i , 角色属于异步组件, 游客不加载这部分数据 -->
        <ul class="user">
          <li title="动态通知/ 事务通知/ 声音开关">通知</li>
          <li title="提案/ 设想/ 思路">创建</li>
          <!-- 消息通知依附于角色 监听用户活动窗口 监听用户交互状态以确定信息是否被成功阅读 -->
          <!-- 非交互状态信息不直接显示 交互状态显示信息并自动收起 -->
          <!-- 隐私设置: 离开时不主动显示消息通知, 交互状态自动将消息设定为已阅读 -->
          <!-- 刚离开一分钟内收到消息的, 检测下一个动作是否在一分钟内结束, 以决定信息正常收起后是否标记为已阅读 -->
          <li title="角色/ 角色属性数据 / 角色中心/设置包括声音/语言"><img src="./assets/logo.png"></li>
        </ul>
      </nav>
    </header>

    <router-view/>

    <footer>
      <!-- 不变的底部 -->
    </footer>
  </div>
</template>

<script>

  export default {
    name: 'App',
    data () {
      return {
        title: 'Welcome to thread',
        author: 'Last',
        content: '主题演讲<img src="/static/back.jpg">',
        attach:[
        { name:'fff', size:'10240bit' }
        ],
        tags:[
        { name: 'tag', id: '88' }
        ],
        navs: [
        { name: 'Home &logo', url:'/', item: '5665465' },
        { name: 'areas', url:'/areas',  item: '5665465' },
        { name: 'project', url:'/project',  item: '5665465' },
        { name: 'idea', url:'/idea',  item: '5665465' },
        { name: 'want', url:'/want',  item: '5665465' },
        { name: 'vision', url:'/vision',  item: '5665465' }
        ],
        relateds: '关联推荐 如标签关联亦或作者关联 亦或各种偏好与算法上的',
      }
    },
    mounted: function () {
      //this.fetchData()
    }
  }

// 亦可在此处载入音频&BGM服务? 应在某个组件中而不是这里
// 登录维持 消息推送服务
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  /*margin-top: 60px;*/
  background: rgba(248,249,251,1);
}
html, body { font-size:12px; padding:0; margin:0; }
header { color: #fff; background-color: #3c4146; border-bottom-color: #202326; display: flex; justify-content: center; }
header>nav { display: flex; width: 1000px ; }
header>nav>ul { flex: 1; list-style: none; margin: 0; padding: 0; }
header>nav>ul:after{ content:"";display:block;clear:both; }
header>nav>ul>li { float: left; padding: 0; margin: 0; }
header>nav>ul>li>a { display: block; padding: 1.5rem 1.5rem; color: #fff; text-decoration: none; }
.user>li { float: right; }
.user>li>img { width:32px; height:32px; }
.logo { font-size: 1rem; padding: 0; color: #24292e; background: #444; }
</style>
