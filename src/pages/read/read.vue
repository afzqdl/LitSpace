<template>
  <!-- 阅读文字区域 -->
  <view class="page" @touchstart="start" @touchend="end"
    :style="{ paddingBottom: padBottom + 'px', paddingTop: padTop + 'px' }">
    <view class="text-area" @click="hiddenTools">
      <text selectable="true">
        {{ contents[readingNow].info }}
        <br>
        {{ readingNow }}
        {{ spaceMsg }}
      </text>
    </view>
    <button class="tools-btn" @click="showTools">↑上滑显示工具栏</button>
    <!-- 下方工具栏 -->
    <view class="tools" v-show="isShowTools" :style="{ paddingBottom: padBottom + 'px' }">
      <view class="space" @click="toViews">景</view>
      <view class="spaceChat-parent">
        <textarea class="spaceChat" v-model="spaceMsg" placeholder="输入文段" maxlength="300" :show-confirm-bar="false"
          auto-height />
      </view>
      <view class="btns">
        <view>章节</view>
        <view>笔记</view>
        <view>进度</view>
        <view>主题</view>
        <view>字体</view>
      </view>
    </view>
    <!-- 导航栏 -->
    <view class="navbar" v-show="isShowTools" :style="{ paddingTop: padTop + 'px' }">
      <view class="back" @click="back">《</view>
      <view>
        <view class="bars">购买</view>
        <view class="bars">书架</view>
        <view class="bars">书友</view>
        <view class="bars">分享</view>
        <view class="bars">更多</view>
      </view>
    </view>
  </view>
</template>

<script>
// import Tools from './components/Tools'

export default {
  name: 'read',
  // components: {
  //   Tools
  // },
  data() {
    return {
      isShowTools: false,
      padBottom: '',
      padTop: '',
      spaceMsg: '',
      contents: [
        {
          info: '这是第一页的内容这是第一页的内容这是第一页的内容\n这是第一页的内容这是第一页的内容这是第一页的内容这是第一页的内容',
          pageNum: 1
        },
        {
          info: '这是第二页的内容这是第二页的内容这是第二页的内容这是第二页的内容这是第二页的内容这是第二页的内容这是第二页的内容',
          pageNum: 2
        },
        {
          info: '这是第三页的内容这是第三页的内容这是第三页的内容这是第三页的内容这是第三页的内容这是第三页的内容这是第三页的内容',
          pageNum: 3
        },
        {
          info: '这是第四页的内容这是第四页的内容这是第四页的内容这是第四页的内容这是第四页的内容这是第四页的内容这是第四页的内容这是第四页的内容',
          pageNum: 4
        },
      ],
      readingNow: 0,
      startData: {
        clientX: '',
        clientY: ''
      }
    }
  },
  methods: {
    start(e) {
      this.startData.clientX = e.changedTouches[0].clientX;
      this.startData.clientY = e.changedTouches[0].clientY;
    },
    end(e) {
      // console.log(e)
      const subX = e.changedTouches[0].clientX - this.startData.clientX;
      const subY = e.changedTouches[0].clientY - this.startData.clientY;
      if (subY > 50) {
        console.log('下滑')
      } else if (subY < -50) {
        console.log('上滑');
        this.isShowTools = true
      } else {
        if (subX > 100) {
          console.log('右滑')
          if (this.readingNow > 0) {
            this.readingNow--
          } else {
            uni.navigateBack({
              delta: 1,
            })
          }
        } else if (subX < -100) {
          console.log('左滑')
          if (this.readingNow < this.contents.length - 1) {
            this.readingNow++
          }

        } else {
          console.log('无效')
        }
      }
    },
    showTools() {
      this.isShowTools = true
    },
    hiddenTools() {
      this.isShowTools = false
    },
    back() {
      uni.navigateBack({
        delta: 1,
      })
    }
  },
  mounted() {
    this.padBottom = uni.getSystemInfoSync().safeAreaInsets.bottom
    this.padTop = uni.getSystemInfoSync().safeAreaInsets.top
  }
}
</script>

<style lang="scss">
Page {
  // padding: 100rpx;
  background-color: #f8f8fa;

}


.page {
  // background-color: pink;
  background-color: #f8f8fa;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  justify-content: center;
}

.text-area {
  // width: 500rpx;
  margin: 60rpx;
  white-space: pre-line;
  color: #161920;
  height: 100%;
}

.tools-btn {
  position: fixed;
  bottom: 50rpx;
  border: 1rpx solid grey;
  width: 250rpx;
  height: 50rpx;
  font-size: 24rpx;
  line-height: 50rpx;
  border-radius: 40rpx;
}

.tools {
  position: absolute;
  width: 100%;
  bottom: 0;
  background-color: #feffff;
  // background-color: pink;
  border-top: 1rpx solid #5c636d;
  padding-top: 20rpx;



  .btns {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    padding: 20rpx 0;
  }

  .btns>view {
    display: inline-block;
    width: 130rpx;
    border: 1rpx solid grey;
    text-align: center;
  }

  .space {
    width: 100rpx;
    height: 100rpx;
    border-radius: 50%;
    line-height: 90rpx;
    text-align: center;
    position: absolute;
    right: 50rpx;
    bottom: 250rpx;
    font-size: 60rpx;
    color: white;
    background-color: #5c636d;
  }

  .spaceChat-parent {
    width: 100%;
    padding: 0 15rpx;
  }

  .spaceChat {
    width: 100%;
    // background-color: pink;
    border: 1rpx solid grey;
  }
}

.navbar {
  position: absolute;
  width: 100%;
  top: 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  background-color: #feffff;
  // background-color: pink;
  padding: 0rpx 30rpx;

  .bars {
    display: inline-block;
    margin: 0 20rpx;
    border: 1rpx solid grey;
    text-align: center;
  }

  .back {
    // font-size: 40rpx;
    font-weight: bold;
  }
}
</style>