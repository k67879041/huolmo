<template>
	<view class="container">
		<view class="logo-container">
			<view class="logo" v-for="(pet, index) in pets" :key="pet.id">
				<image class="logo-ba" :src="pet.url"  mode="widthFix" @click="onPreview(index)">{{pet.id}}</image>
				<text class="title">demo2测试</text>
			</view>
		</view>
		
	</view>
</template>

<script setup>
import { ref } from 'vue'
const pets = ref([]);
const title = ref('demo2测试');
let petsCount = 10;



const onPreview = function(index) {
	console.log(index)
	let urls = pets.value.map(item => item.url);
	uni.previewImage({
		urls: urls,
		current: urls[index]
	})
}


// 测试API接口
function testApi() {
  uni.request({
    url: 'https://api.thecatapi.com/v1/images/search',
   // method: 'GET',
	data: {
		limit: 10
	},
    success: (res) => {
      console.log(res)
      pets.value = res.data;
    }
 	})
}
// 调用API接口获取数据
testApi();
</script>

<style lang="scss" scoped>
.container {
	.logo-container {
		// 垂直居中图片和文字
		padding: 50rpx;
		.logo {
			// 垂直居中图片和文字
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			margin-bottom: 50rpx;
			box-shadow: 0 0 10rpx rgba(0, 0, 0, 0.5);
			border-radius: 10rpx;
			overflow: hidden;
		}
		.logo-ba {
			height: 400rpx;
			width: 400rpx;
		}
	}
	.title {
		// 下一行居中
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 20rpx 0;
		font-size: 36rpx;
		color: #8f8f94;
	}
}
</style>