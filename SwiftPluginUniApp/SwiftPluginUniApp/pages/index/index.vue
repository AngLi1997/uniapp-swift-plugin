<template>
	<view>
		<view style="padding: 20px;">
			<input v-model="command" placeholder="输入命令" />
			<button style="margin-top: 20px;" type="primary" @click="sendCommand">发送</button>
		</view>
	</view>
</template>

<script>
	// 首先需要通过 uni.requireNativePlugin("ModuleName") 获取 module 
	var plugin = uni.requireNativePlugin("SwiftPlugin-SwiftEntrance")

	export default {
		data() {
			return {
				command: '',
			}
		},
		onLoad() {

		},
		methods: {
			sendCommand() {
				console.log(this.command);
				plugin.sendCommand({
						'name': 'uni-app',
						'command': this.command
					},
					(result) => {
						uni.showToast({
							title: result,
							icon: "none"
						})
					})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
