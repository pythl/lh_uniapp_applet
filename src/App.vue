<script>
export default {
    globalData: {
        statusBarHeight: 0, // 状态导航栏高度
        navHeight: 0, // 总体高度
        navigationBarHeight: 0, // 导航栏高度(标题栏高度)
        isLogin: false, //是否登录
        chatName: '赛事天下',
    },
    onLaunch: function () {
        console.log('App Launch');
        // 状态栏高度
        this.globalData.statusBarHeight = uni.getSystemInfoSync().statusBarHeight;

        // #ifdef MP-WEIXIN
        // 获取微信胶囊的位置信息 width,height,top,right,left,bottom
        const custom = wx.getMenuButtonBoundingClientRect();
        // console.log(custom)

        // 导航栏高度(标题栏高度) = 胶囊高度 + (顶部距离 - 状态栏高度) * 2
        this.globalData.navigationBarHeight = custom.height + (custom.top - this.globalData.statusBarHeight) * 2;
        // console.log("导航栏高度："+this.globalData.navigationBarHeight)

        // 总体高度 = 状态栏高度 + 导航栏高度
        this.globalData.navHeight = this.globalData.navigationBarHeight + this.globalData.statusBarHeight;
        // #endif
    },
    onShow: function () {
        console.log('App Show', this.globalData);
    },
    onHide: function () {
        console.log('App Hide');
    },
};
</script>

<style lang="scss">
/* 注意要写在第一行，同时给style标签加入lang="scss"属性 */
@import 'uview-ui/index.scss';
/*每个页面公共css */
@import './static/css/base.scss';
/* scss公共类 */
@import './static/css/common.scss';
</style>
