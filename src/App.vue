<template>
  <div id="app">
        <Modal></Modal>
        <nav class="navbar navbar-default navbar-fixed-top">
            <div class="container-fluid">
                <div class="navbar-header">
                    <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-navbar-collapse" aria-expanded="false">
                        <span class="sr-only">{{ $t("action.toggleNavbar") }}</span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                    </button>
                    <router-link class="navbar-brand" to="/">{{ $t("info.title") }}</router-link>
                </div>
                
                <div class="collapse navbar-collapse" id="bs-navbar-collapse">
                    <ul class="nav navbar-nav">
                        <li><a href="https://space.bilibili.com/1926156228/" target="_blank" rel="nofollow"><img src="resources/bilibili_logo_x64.png" height="18"/></a></li>
                        <li><a href="https://weibo.com/u/7544721964" target="_blank" rel="nofollow"><img src="resources/weibo_logo_x64.png" height="18"/></a></li>
                        <li><a href="https://twitter.com/_Ciyana" target="_blank" rel="nofollow"><img src="resources/twitter_logo_x200.png" height="18"/></a></li>
                        <li><a href="https://zh.moegirl.org.cn/%E5%B8%8C%E4%BA%9A%E5%A8%9CCiyana" target="_blank" rel="nofollow"><img src="resources/moegir_logo_x80.png" height="18"/></a></li>
						<li><a href="https://afdian.net/@luomuyu" target="_blank" rel="nofollow"><img src="resources/afdian_logo_x80.png" height="18"/></a></li>
                    </ul>
                    <ul class="nav navbar-nav navbar-right">
                        <li class="dropdown">
                            <a href="javascript:;" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">{{$t("lang." + currentLang)}} <span class="caret"></span></a>
                            <ul class="dropdown-menu">
                                <li><a href="javascript:;" @click="chlang('zh-CN')">{{$t("lang.zh-CN")}}</a></li>
                                <!--<li><a href="javascript:;" @click="chlang('en-US')">{{$t("lang.en-US")}}</a></li>-->
                                <li><a href="javascript:;" @click="chlang('ja-JP')">{{$t("lang.ja-JP")}}</a></li>
                            </ul>
                        </li>
                    </ul>
                </div>

            </div>
        </nav>
        <div class="container-fluid main-content">
            <router-view></router-view>
        </div>
        <footer class="footer">
            <div class="container-fluid footer-content" style="text-align:center">
                <div><a href="https://beian.miit.gov.cn/" target="_blank" rel="nofollow">冀ICP备20002037号-2</a></div>
				<div>Copyright © 2020 <a href="https://www.luomuyu.xyz" target="_blank" rel="nofollow">洛沐语.</a>All Rights Reserved.</div>
            </div>
        </footer>
  </div>
</template>

<style lang="scss">
@import "../node_modules/bootstrap/dist/css/bootstrap.css";
body{
    padding-top: 70px;
}
.main-content{
    min-height: 100vh;
}
.footer {
    width: 100%;
    height: 60px;
    background-color: #ebebeb;
}
.footer-content {
    padding-top: 10px;
    color: #666;
}
.text-right{
    text-align: right;
}
::-webkit-scrollbar{
	display:none;
}
</style>

<script>
import Vue from 'vue'
import Component from 'vue-class-component'
import Modal from './components/modal.vue'
//import fetchpost from './util/fetchpost'

@Component({
    components:{
        Modal
    }
})
class App extends Vue {
    get currentLang(){
        return this.$i18n.locale;
    }
    created(){
        // eslint-disable-next-line 
        console.log("Produced by Luomuyu");
        this.$i18n.locale = localStorage.getItem("lang") || this.$i18n.locale;
    }
    chlang(v){
        this.$i18n.locale = v;
        localStorage.setItem("lang", v);
    }
}

export default App;
</script>

