<script>
export default {
    name: 'Fond',
    data() {
        return {
            current: 0, // 标识当前选中的图片序列号
            swipers: [{
                src: '../../../static/images/wdqk3.jpg',
                title: '武之极，破苍穹，动乾坤！'
            }, {
                src: '../../../static/images/jianlai2.jpg',
                title: '大千世界，无奇不有，我陈平安，唯有一剑'
            }, {
                src: '../../../static/images/saye.jpg',
                title: '我想我们都应该勇敢'
            }, {
                src: '../../../static/images/xianwang2.png',
                title: '面对困难，王令会碾压对手？还是低调的躺倒装死？'
            }],
            toolImages: [
                {
                    src: '../../../static/font-icon/note.png',
                    bgc: '#f4ea2a',
                    title: '小说'
                },
                {
                    src: '../../../static/font-icon/sanwen.png',
                    bgc: 'green',
                    title: '散文'
                },
                {
                    src: '../../../static/font-icon/pen.png',
                    bgc: 'skyblue',
                    title: '诗歌'
                },
                {
                    src: '../../../static/font-icon/more.png',
                    bgc: '#d4237a',
                    title: '更多'
                }
            ]
        }
    },
    onLoad() {
    },
    methods: {
        // changeIndicatorDots方法会在轮播的图片切换后调用，e.detail.current表示当前所在滑块的 index
        changeIndicatorDots(e) {
            this.current = e.detail.current
        }
    }
}
</script>

<template>
    <!-- 轮播图组件 -->
    <view class="swiper-current">
        <swiper class="swiper-box" :autoplay="true" :interval="3000" :duration="500" circular indicator-dots
            indicator-active-color="#011500" :disable-touch="true" style="height: 250rpx;" @change="changeIndicatorDots">
            <swiper-item v-for="(item, index) in swipers" :key="index">
                <image :src="item.src" mode="sapectFill" style="height:250rpx;width: 100%;" class="rounded-lg">
                </image>
            </swiper-item>
        </swiper>
        <view class="swiper-bottom">
            <view class="title">{{ swipers[current].title }}</view>
        </view>
    </view>

    <!-- tools -->
    <view class="tools">
        <view class="tool" v-for="(imgs, index) in  toolImages " :key="index" :style="{ backgroundColor: imgs.bgc }">
            <image class="tool-icon" :src="imgs.src" mode="scaleToFill" />
            <view class="img-title">{{ imgs.title }}</view>
        </view>
    </view>

    <!-- 热门推荐 -->
    <view class="recommend">
        <view class="recommend-top">
            <text>热门推荐</text>
            <text class="recommand-more">更多></text>
        </view>
        <view class="items">
            <view class="rec-item">
                <image src="../../../static/images/shenmu.jpg" />
                <view class="rec-title">神墓</view>
                <view class="author">作者：辰东</view>
            </view>
            <view class="rec-item">
                <image src="../../../static/images/wzdmxcsa.jpg" />
                <view class="rec-title">我真的没想重生啊</view>
                <view class="author">作者：莫默</view>
            </view>
            <view class="rec-item">
                <image src="../../../static/images/xianwang.png" />
                <view class="rec-title">仙王的日常生活</view>
                <view class="author">作者：枯玄</view>
            </view>

        </view>
    </view>

    <!-- <view class="recommend">
        <view class="recommend-top">
            <text>经典推荐</text>
            <text class="recommand-more">更多></text>
        </view>
        <view class="items">
            <view class="rec-item">
                <image src="../../../static/images/sywz2.png" />
                <view class="rec-title">神印王座2皓月当空</view>
                <view class="author">作者：唐家三少</view>
            </view>
            <view class="rec-item">
                <image src="../../../static/images/bezc.png" />
                <view class="rec-title">不二之臣</view>
                <view class="author">作者：不只是棵菜</view>
            </view>
            <view class="rec-item">
                <image src="../../../static/images/winter.png" />
                <view class="rec-title">济南的冬天</view>
                <view class="author">作者：老舍</view>
            </view>

        </view>
    </view> -->
</template>

<style lang="scss">
.uni-margin-wrap {
    width: 690rpx;
    width: 100%;
}

.swiper {
    height: 300rpx;
}

.swiper-item {
    display: block;
    height: 300rpx;
    line-height: 300rpx;
    text-align: center;
}

.swiper-box {
    box-shadow: 0rpx 50rpx rgba($color: #a29e9e, $alpha: 0.5);
}


.swiper-bottom>.title {
    width: 600rpx;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}

//热门推荐部分样式
.recommand-more {
    float: right;
}

.items {
    display: flex;
}

.rec-item {
    // width: 220rpx;
    // height: 330rpx;
    display: inline-block;
    margin-left: 30rpx;
    margin-top: 30rpx;
    background-color: #f5f5f5;
    text-align: center;
    vertical-align: middle;
    border-radius: 10px;
}

.rec-item>image {
    width: 180rpx;
    height: 240rpx;
}

// .item view {
//     width: 200rpx;
// }

.rec-title {
    width: 200rpx;
    // margin-left: 60rpx;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;

}

.author {
    font-size: 13px;
    color: #716f70;
}

.recommend {
    background-color: #d3ddef;
    padding: 10rpx;
    padding-bottom: 13px;
    margin: 10px;
    border-radius: 10px;
    box-shadow: 6rpx 6rpx 6rpx black;
}

.tools {
    // background-color: #fbfbfb;
    padding: 15rpx;
    // margin: 10px;
    // border-radius: 10px;
    // box-shadow: 6rpx 6rpx 6rpx black;
    // border-top: 5px solid #fbfbfb;
    // border-bottom: 5px solid #ebe3e3;
    display: flex;
    padding-bottom: 40rpx;
    margin-top: 30rpx;
    box-shadow: 8rpx 0rpx 6rpx black;
}

.tool {
    width: 90rpx;
    height: 90rpx;
    // background-color: skyblue;
    text-align: center;
    border-radius: 30%;
    margin: auto;
}

.tool-icon {
    width: 60rpx;
    height: 70rpx;
    line-height: 90rpx;
    margin-bottom: 5rpx;
}

.img-title {
    color: #716363;
    font-size: 30rpx;
    margin-top: 20rpx;
}
</style>
