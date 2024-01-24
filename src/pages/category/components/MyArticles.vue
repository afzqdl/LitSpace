<template lang="">
    <view class="ArticleList">
		<view class="cards">
			<view class=card v-for="(card, index) in cardArticles" :key="index">
				<view class="card-title">{{ card.title }}</view>
				<image class="cover-img" :src="card.src" mode="scaleToFill" />
				<view class="article">
					{{ card.article }}
				</view>
			</view>
		</view>
    </view>
</template>

<script>
export default {
	name: 'MyArticles',
	data() {
		return {
			cardArticles: [
				{
					title: '小昙',
					src: '../../../static/images/shikodi.jpg',
					article: '她只走向有“你”在的未来'
				},
				{
					title: '啊噗鲁派！！',
					src: '../../../static/images/party.jpg',
					article: '美酒，美食，好朋友......对了，还有用来交换的礼物。准备万全，派对时间到！！'
				},
				{
					title: '春弦',
					src: '../../../static/images/szr.jpg',
					article: '纵使冬日寒夜漫漫，温暖的阳光总会穿透云层，带领我们抵达春天'
				}
			]
		}
	},
}

</script>

<style lang="scss">
.ArticleList {

	margin-top: 210rpx;
	// background-color: blue;
	padding-bottom: 100rpx;

}

.card {
	background-color: #e2e7ee;
	padding: 20rpx;
	margin: 30rpx;
	border-radius: 10px;
	text-align: center;
	// border: 3px solid #ebeef5;
	box-shadow: 3px 3px 3px #898b90;
}

.cover-img {
	width: 80%;
	height: 300rpx;
	margin-top: 74rpx;
}

.article {
	margin-top: 20rpx;
	width: 90%;
	display: inline-block;
	font-size: 26rpx;
	color: #716f70;
}

.card-title {
	width: 530rpx;
	position: absolute;
	padding-bottom: 3px;
	left: 15%;
	border-bottom: 2px solid rgb(99, 90, 90);
	text-align: left;
	font-size: 40rpx;
	color: #353334
}
</style>