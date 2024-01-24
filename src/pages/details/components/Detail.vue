<template>
    <view class="header">
        id = {{ bookInfo.id }}
    </view>
    <view class="footer" :style="{ paddingBottom: padBottom + 'px' }">
        <button>加入书架</button>
        <button class="read">阅读</button>
    </view>
</template>

<script>
export default {
    name: 'Detail',
    data() {
        return {
            padBottom: 1,
            bookInfo: {
                id: 'bookId'
            }
        }
    },
    onLoad(option) {
        console.log("hhh");
    },
    methods: {

    },
    mounted() {
        this.padBottom = uni.getSystemInfoSync().safeAreaInsets.bottom
    }
}
</script>

<style lang="scss">
.footer {
    width: 100%;
    position: fixed;
    bottom: 0;
    text-align: center;
    background-color: #fefefe;
    padding-top: 20rpx;
    border-top: 1rpx solid grey;

    button {
        background-color: #f5f5f5;
        width: 40%;
        display: inline-block;
        margin: 0 20rpx;
        font-size: 30rpx;
    }

    .read {
        background-color: #008bfa;
        color: #fefefe;
    }
}
</style>