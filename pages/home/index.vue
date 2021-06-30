<template>
	<div>
		<div class="header">
			<span>豆瓣</span>
			<icon type="search" size="16" color="#00b600">
			</icon>
			<button>打开豆瓣App</button>
		</div>
		<div class="movie-item">
			<div class="title">
				<div>影院热映</div>
				<div class="more">更多</div>
			</div>
			<scroll-view class="scroll-view_H" scroll-x="true" bindscroll="scroll" style="width: 100%">
				<div id="demo1" class="scroll-view-item_H demo-text-1" v-for="(item,index) in 6" :key="index">
					<img src="https://img2.doubanio.com/view/photo/m_ratio_poster/public/p2641407963.jpg" />
					<p class="text-line1">哆啦A梦：伴我行</p>
					<div class="rating">
						<div class="stars">
							<img src="../../static/image/star.svg" v-for="(item2,i) in 5" :key="index" />
						</div>
						<span>6.3</span>
					</div>
				</div>
			</scroll-view>
		</div>
	</div>
</template>

<script>
	export default {
		created() {
			this.getMovie()
		},
		data() {
			return {

			}
		},
		methods: {
			getMovie() {
				wx.request({
					url: 'https://api.douban.com/v2/movie/in_theaters?apikey=0df993c66c0c636e29ecbb5344252a4a',
					header: {
						'Content-Type': 'application/x-www-form-urlencoded'
					},
					success: res => {
						console.log(res)
					},
					fail:res => {
						console.log(1)
					}
				})
			}
		}
	}
</script>

<style lang="less">
	.header {
		display: flex;
		border-bottom: 1px solid #eee;
		height: 95rpx;
		align-items: center;
		padding: 0 36rpx;

		span {
			font-weight: 700;
			color: #00b600;
			font-size: 40rpx;
		}

		icon {
			margin-left: 28rpx;
			flex: 1;
		}

		button {
			background-color: #42bd56;
			color: #fff;
			height: 58rpx;
			width: 200rpx;
			border-radius: 8rpx;
			line-height: 58rpx;
			marigin-right: 36rpx;
		}
	}

	.movie-item {
		padding: 0 36rpx;

		.title {
			font-size: 32rpx;
			display: flex;
			height: 88rpx;
			justify-content: space-between;
			align-items: center;

			.more {
				font-size: 28rpx;
				color: #00b600;
			}
		}
	}

	.page-section-spacing {
		margin-top: 60rpx;
	}

	.scroll-view_H {
		white-space: nowrap;
	}

	.scroll-view-item {
		height: 300rpx;
	}

	.scroll-view-item_H {
		display: inline-block;
		margin-right: 18rpx;
		margin-top: 18rpx;
		width: 200rpx;

		img {
			width: 200rpx;
			height: 286rpx;
		}

		p {
			text-align: center;
		}

		.rating {
			display: flex;
			justify-content: center;

			.stars {
				img {
					height: 20rpx;
					width: 20rpx;
				}
			}

			span {
				color: #aaa;
				margin-left: 10rpx;
			}
		}

	}
</style>
