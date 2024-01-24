<template>
    <view class="header">
        <image :src="bookInfo.img" mode="scaleToFill" />
        <view class="info">
            <view class="title">{{ bookInfo.title }}</view>
            <view class="author">{{ bookInfo.author }}</view>
            <view class="introduction">{{ bookInfo.introduction }}</view>
        </view>
    </view>
    <view class="recommend">
        <view>读书推荐值：{{ bookInfo.recommend }}%</view>
    </view>
    <view class="comments">
        <text class="comments-font">精彩点评</text>
        <text class="comments-Num">{{ bookInfo.comments.num }}个></text>
        <view class="content" v-for="(comment, index) in bookInfo.comments.shownComments" :key="index">
            <image :src="comment.userPhoto" mode="scaleToFill" />
            <text class="name">{{ comment.username }}</text>
            <text class="rec" v-if="comment.recommend === 1">: )</text>
            <text class="recommend" v-else-if="comment.recommend === 2">: |</text>
            <text class="recommend" v-else>: (</text>
            <view class="main-content">{{ comment.content }}</view>
        </view>
        <view class="more">查看更多精彩点评</view>
    </view>
    <view class="author-more">
        <text class="author">{{ bookInfo.author }}</text>
        <text class="num">·{{ bookInfo.authormore }}个作品></text>
        <button class="subscribe">+ 订 阅</button>
    </view>
    <view class="footer" :style="{ paddingBottom: padBottom + 'px' }">
        <button>加入书架</button>
        <button class="read" @click="toRead">阅读</button>
    </view>
</template>

<script>
export default {
    name: 'Detail',
    data() {
        return {
            padBottom: 1,
            bookInfo: {
                id: 'bookId',
                img: '../../static/images/wzdmxcsa.jpg',
                title: '我真没想重生啊',
                author: '柳岸花又明',
                introduction: '万万没想到，社会精英、钻石单身汉的陈汉升居然重生了，一觉醒来变成了高三毕业生。十字路口的陈汉升也在犹豫，宝藏女孩沈幼楚和白月光萧容鱼，应该选择谁？',
                recommend: '92.3',
                comments: {
                    num: '540',
                    shownComments: [
                        {
                            userPhoto: '../../static/images/userphoto1.jpg',//用户头像
                            username: '。',
                            recommend: 1,//该用户的是否推荐,1推荐，2一般，3不行
                            comment: '641',//评论
                            like: '765',//点赞
                            content: '各位老哥，推荐一下有没有可以媲美这本小说的？书荒了！！！！  重生的可以接受，但不要什么兵王啊都市什么战神啊，什么赘婿啊，什么异能啊，看到这些就讨厌。推荐一些文笔好的接地气的。谢谢！' //内容
                        },
                        {
                            userPhoto: '../../static/images/userphoto2.jpg',//用户头像
                            username: '也朝',
                            recommend: 1,//该用户的是否推荐,1推荐，2一般，3不行
                            comment: '4',//评论
                            like: '24',//点赞
                            content: "这是一个令人羡慕的人生，但不是一个正确的例子。在爱情零落的时代，满地都是粘尘的玫瑰。白齿青眉时难觅一川风月，后来的月约星期不过是相儒相呴。我只能说陈汉生真的渣。但社会现实确实如此，中多次提到过，只有足够的资金才能让他进行下面的动作，就只证明了一点。这是有钱人的爱情。但如果抛开文章总的剧情来看，文中所有女生和男主的促进单拉出来都是完美的，有傲娇的白月光，成了律所的萧主任，宝藏女孩也有勇气抬头面对所有人，" + "罗师妹读了心理变得没有那么偏执，大女儿也得到了他应有的救赎。落难公主摆脱了落难二字，成了小米的王后。孔姐最后也直面了当年的遗憾。金钱至上的普通人黄慧，老实人鸡脖，和同样骄傲的湘妹子总于有了一个结果，两个只会喔喔叫的小孩儿真的很容易让人把心化掉。文章很写实，人物形象栩栩如生。里面出现的每一个女孩，" +
                                "在我们普通人眼里，都是值得托付终身的人。男主的行为才那么让人痛恨。像我们都经历过白月光和宝藏的时代。两拳法对现实中普通的我们真的很难做到。一本书的意义不只在于读的过程中的喜怒哀乐，也在于它的现实意义，他在告诉我们浮生若梦，珍重你的选择。是白月光还是朱砂痣？不过是你。在关键节点的选择，选择过后否能做到一生只待一人。他也很现实的告诉你人际交往关系不是只浮于表面。最后真的存在很多不那么童话的东西。简而言之：文笔 细节描写：8分 剧情6分 我之前给了一个一般 但是还是舍不得我的小鱼儿啊 给个推荐吧。" //内容
                        },
                        {
                            userPhoto: '../../static/images/userphoto3.jpg',//用户头像
                            username: '南无萨摩耶',
                            recommend: 1,//该用户的是否推荐,1推荐，2一般，3不行
                            comment: '3',//评论
                            like: '13',//点赞
                            content: '四颗星，如果不是前期够神还得减分。前期很出色，后期崩，，以后期主角的地位，情商和能力，不应该费这么大力气才搞定二女。其中沈楚幼，就根本不应该花什么力气。主角对她，根本就是再造之恩了。至于另一个女主小鱼，我压根觉得她就不配当女主。前期主角没有地位时，这样描写很正常，后期还这么处理那就是扯淡了。作者后期对时代大佬的地位，也完全没点数。地位与情节不匹配，所以后期剧情崩，而且违和。说到人物，说到主角，'
                                + '口口声声说写渣男，哪里有这么可怜的渣男。付出那么多，财富那么多，结果没有一点地位可言，生的都是女儿等等，以及后期大段大段女儿奴描写，其实说白了，在讨好一些女性读者罢了。强行把亿万富翁，写成舔狗屌丝那些所谓的女主，除了所谓的长得漂亮，到底为主角付出了什么？我尤其不喜欢所谓的白月光。还不如那两个事业上女配，给了主角最大帮助，渣男？可怜虫罢了。'
                                + '沈楚幼，除了貌美心善，就是拖油瓶。无社交能力无情商，小鱼，日常耍小性。不是强行开律师大佬挂也基本拖后腿。罗璇，整就一神经病。这个人物完全删掉都没什么问题，没有一点点可取的地方。商妍妍，花瓶，强行情人就算了，还特意设定为破鞋。堂堂重生行业大佬，女人就这种歪瓜裂枣。'
                                + '为陈狗感到不值.。' //内容
                        }
                    ]
                },
                authormore: 2//作者还有多少作品
            }
        }
    },
    onLoad(option) {
        this.bookInfo.id = option.id
    },
    methods: {
        toRead() {
            uni.navigateTo({
                url: '../read/read',
            })
        }
    },
    mounted() {
        this.padBottom = uni.getSystemInfoSync().safeAreaInsets.bottom
    }
}
</script>

<style lang="scss">
Page {
    background-color: #f3f4f6;
    padding-bottom: 250rpx;
}

.header {
    padding: 20rpx 50rpx;
    background-color: #fefefe;

    image {
        width: 200rpx;
        height: 320rpx;
        border: 1rpx solid #988f88;
        box-shadow: 1rpx 1rpx 10rpx #717882;
        margin-bottom: 30rpx;
    }

    .info {
        width: 420rpx;
        float: right;
        // background-color: pink;
        margin-bottom: 30rpx;

        .author {
            margin: 14rpx 5rpx;
            font-size: 26rpx;
            color: #1a87ec;
        }

        .title {
            color: #0d141e;
            font-size: 40rpx;
        }

        .introduction {
            height: 75rpx;
            margin: 14rpx 5rpx;
            font-size: 28rpx;
            color: #717882;
            overflow: hidden; //溢出隐藏
            text-overflow: ellipsis; //省略号
            display: -webkit-box; //
            -webkit-box-orient: vertical; //设置弹性盒子的子元素的排列方式
            -webkit-line-clamp: 2; //设置显示文本的行数
        }
    }
}

.recommend {
    padding: 20rpx 50rpx;
    background-color: #fefefe;
    margin-top: 20rpx;
}

.comments {
    padding: 20rpx 50rpx;
    background-color: #fefefe;
    margin-top: 20rpx;
    // padding-bottom: 500rpx;

    text {
        font-size: 26rpx;
        margin-right: 10rpx;
    }

    .comments-Num {
        color: #9a9fa6;
    }

    .content {
        background-color: #f6f6f6;
        padding: 20rpx;
        border-radius: 20rpx;
        margin: 20rpx 0;

        image {
            width: 45rpx;
            height: 45rpx;
            border-radius: 50%;
            margin-right: 20rpx;
        }

        .name {
            margin-right: 20rpx;
        }

        .main-content {
            color: #131a22;
            font-size: 30rpx;
            padding: 0 15rpx;
            margin: 15rpx 0;
            overflow: hidden;
            text-overflow: ellipsis;
            -webkit-line-clamp: 5;
            display: -webkit-box;
            -webkit-box-orient: vertical;
        }
    }

    .more {
        background-color: #f6f6f6;
        padding: 20rpx;
        border-radius: 20rpx;
        margin: 20rpx 0;
        text-align: center;
        font-size: 24rpx;
    }
}

.author-more {
    padding: 20rpx 50rpx;
    background-color: #fefefe;
    margin-top: 20rpx;

    .author {
        font-size: 30rpx;
        line-height: 60rpx;
    }

    .num {
        font-size: 24rpx;
        margin-left: 14rpx;
        color: #989fa9;
        line-height: 60rpx;
    }

    .subscribe {
        display: inline-block;
        height: 60rpx;
        font-size: 26rpx;
        line-height: 60rpx;
        float: right;
        color: white;
        background-color: #0092f9;
        border-radius: 30rpx;
    }
}

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