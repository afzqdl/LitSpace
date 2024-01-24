<script>
export default {
    name: 'NavBar',
    data() {
        return {
            tag: '1',
            padTop: 1,
            showRight: false,
            showLeft: false
        }
    },
    methods: {

        confirm() { },
        // 打开窗口
        showDrawer(e) {
            this.$refs[e].open()
        },
        // 关闭窗口
        closeDrawer(e) {
            this.$refs[e].close()
        },
        // 抽屉状态发生变化触发
        change(e, type) {
            console.log((type === 'showLeft' ? '左窗口' : '右窗口') + (e ? '打开' : '关闭'));
            this[type] = e
        }

    },
    mounted() {
        this.padTop = uni.getSystemInfoSync().safeAreaInsets.top
    },
    onNavigationBarButtonTap(e) {
        if (this.showLeft) {
            this.$refs.showLeft.close()
        } else {
            this.$refs.showLeft.open()
        }
    },
    // app端拦截返回事件 ，仅app端生效
    onBackPress() {
        if (this.showRight || this.showLeft) {
            this.$refs.showLeft.close()
            this.$refs.showRight.close()
            return true
        }
    }
}
</script>

<template>
    <view class="navbar" :style="{ paddingTop: padTop + 'px' }">
        <view class="nav-top">
            <image class="logo" src="../../../static/images/logo2.png" mode="scaleToFill" />
            <view class="example-body">
                <!-- <image class="img-more" @click="showDrawer('showLeft')" src="../../../static/font-icon/setting.png"
                    mode="scaleToFill" /> -->
                <uni-icons @click="showDrawer('showLeft')" type="bars" color="" size="24" />

                <uni-drawer ref="showLeft" mode="left" :width="320" @change="change($event, 'showLeft')">
                    <!-- <view class="close">
                        <button @click="closeDrawer('showLeft')"><text class="word-btn-white">关闭Drawer</text></button>
                    </view> -->

                </uni-drawer>
            </view>

            <!-- <view class="title">写作</view> -->
            <uni-icons class="more" type="more-filled" size="24" />
            <uni-icons class="sear" type="search" size="24" />

            <!-- <text class="icon-search"></text> -->
            <!-- <uni-icons type="bars" size="30"></uni-icons>
        <uni-icons type="search" size="30"></uni-icons>
        <uni-icons type="more-filled" size="30"></uni-icons> -->

        </view>

    </view>
</template>

<style lang="scss">
.nav-top text {
    margin: 0 5px;
}

.nav-tag {
    margin-top: 15rpx;
    display: flex;
}

.nav-tag text {
    text-align: center;
    width: 115rpx;
    margin: auto;
    padding-bottom: 15rpx;

}

.active {
    border-bottom: 3px solid white;
    text-align: center;
    width: 115rpx;
    margin: auto;
    padding-bottom: 15rpx;
}

.more {
    margin: 0 15rpx;
    float: right;
}

.sear {
    margin: 0 15rpx;
    float: right;
}

.navbar {
    // padding-top: 15rpx;
    width: 100%;
    color: #f7fefe;
    background-color: #44e6da;
    position: fixed;
    top: 0;
    z-index: 2;
    padding-bottom: 30rpx;
}

.normal-view {
    // margin-top: 138px;
    position: absolute;
    top: 18%;
    z-index: 1;
}

.nav-top {
    padding: 10px;
    height: 100rpx;
    background-color: #44e6da;
}



.img-more {
    width: 24px;
    height: 24px
}

.example-body .title .more .sear {
    // background-color: rgb(70, 131, 238);
    display: inline-block;
    // padding: 10px;
}



.example-body {
    position: absolute;
}

.title {
    display: inline-block;
    margin-left: 80rpx;
}

.scroll-view {
    /* #ifndef APP-NVUE */
    width: 100%;
    height: 100%;
    /* #endif */
    flex: 1
}

// 处理抽屉内容滚动
.scroll-view-box {
    flex: 1;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
}

.info {
    padding: 15px;
    color: #666;
}

.info-text {
    font-size: 14px;
    color: #666;
}

.info-content {
    padding: 5px 15px;
}

.close {
    padding: 10px;
}

.logo {
    position: absolute;
    top: 66rpx;
    left: 280rpx;
    width: 185rpx;
    height: 112rpx;
    // z-index: 0;
}
</style>
