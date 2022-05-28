<template>
	<view class="content">
		<view class="box" style="margin-top: 20rpx;">
			friver常用模板
		</view>
		<view class="box">
			引入uView <u-icon name="level" color="red"></u-icon>
		</view>
		<view class="box">
			引入tmUI-vuetify <tm-icons size="64" name="icon-ios"></tm-icons>
		</view>
		<view class="box">
			引入colorUI <text class="cuIcon-deletefill"></text>
		</view>
		<view class="box">
			引入本地数据库
			<input type="text" v-model="word" maxlength="8" />
			<view class="cu-btn sm blue" @click="writeWord">
				提交
			</view>
			<view class="cu-btn sm red" @click="deleteWords()">
				删除
			</view>
			<view class="">
				以下是写入的本地数据:
			</view>
			<view v-for="(item,index) in words" :key="index">
				{{item.word}}
			</view>
		</view>





	</view>
</template>

<script>
	const localDB = require('js/localDB.js')
	const _ = localDB.command
	export default {
		data() {
			return {
				word: '',
				words: []
			}
		},
		onLoad() {
			localDB.init() // 初始化
			this.wordsDB = localDB.collection('words');
			if (!this.wordsDB)
				this.wordsDB = localDB.createCollection('words');
			this.getWOrds()
		},
		methods: {
			writeWord() {
				if (this.word != '') {
					this.wordsDB.add({
						word: this.word
					});
					this.word = '';
					this.getWOrds();
				}
			},

			deleteWords() {
				this.wordsDB.remove();
				this.getWOrds()
			},

			// 渲染words数据
			getWOrds() {
				this.words = this.wordsDB.get()
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

	.box {
		width: 300rpx;
		height: 100rpx;
	}

	input {
		background-color: #EEEEEE;
		/* width: 200rpx; */
		margin: 10rpx 0;
	}
</style>
