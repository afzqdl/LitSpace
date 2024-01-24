<script>
export default {
    name: 'Normal',
    data() {
        return {
            books: [
                {
                    id: '001',
                    title: '活着',
                    author: '余华',
                    img: '../../../static/images/alive.jpg'
                },
                {
                    id: '002',
                    title: '从百草园到三味书屋',
                    author: '鲁迅',
                    img: '../../../static/images/3smellBookHouse.jpg'
                },
                {
                    id: '003',
                    title: '短歌行',
                    author: '曹操',
                    img: '../../../static/images/dgx.jpg'
                },
                {
                    id: '004',
                    title: '神墓',
                    author: '辰东',
                    img: '../../../static/images/shenmu.jpg'
                },
                {
                    id: '005',
                    title: '我真没想重生啊',
                    author: '莫默',
                    img: '../../../static/images/wzdmxcsa.jpg'
                },
                {
                    id: '006',
                    title: '仙王的日常生活',
                    author: '枯玄',
                    img: '../../../static/images/xianwang.png'
                },
                {
                    id: '007',
                    title: '济南的冬天',
                    author: '老舍',
                    img: '../../../static/images/winter.png'
                },
                {
                    id: '008',
                    title: '神印王座2皓月当空',
                    author: '唐家三少',
                    img: '../../../static/images/sywz2.png'
                },
                {
                    id: '009',
                    title: '不二之臣',
                    author: '不只是棵菜',
                    img: '../../../static/images/bezc.png'
                },
                {
                    id: '010',
                    title: '恰似寒光遇骄阳',
                    author: '囧囧有妖',
                    img: '../../../static/images/qshgyjy.png'
                },
            ]
        }
    },
    methods: {
        // toDetail() {
        //     uni.navigateTo({
        //         url: '../details/details',
        //     })
        // }
    }

}
</script>
    
<template>
    <view class="btn-add">+</view>
    <view class="items" v-for="book in books" :key="book.id">
        <navigator class="item" :url="`../details/details?id=${book.id}`">
            <image :src="book.img" />
            <view class="title">{{ book.title }}</view>
            <view class="author">{{ book.author }}</view>
        </navigator>




        <!-- <text>
            这里是Normal
        </text> -->
    </view>
</template>

<style lang="scss">
.items {
    // background-color: #dee1e6;
    display: inline-block;
}

.item {
    // width: 330rpx;
    // height: 500rpx;
    margin-left: 30rpx;
    margin-top: 30rpx;
    // background-color: #f5f5f5;
    text-align: center;
    vertical-align: middle;
}

image {
    width: 190rpx;
    height: 260rpx;
    padding: 10rpx;
    // border-radius: 10px;
}

.title {
    width: 190rpx;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;

}

.author {
    font-size: 13px;
    color: #716f70;
    width: 190rpx;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.btn-add {
    font-size: 36px;
    color: white;
    text-align: center;
    width: 50px;
    height: 50px;
    line-height: 44px;
    background-color: #f6373a;
    border-radius: 25px;
    position: fixed;
    bottom: 50rpx;
    right: 50rpx;
}
</style>