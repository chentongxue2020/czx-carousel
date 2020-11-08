<template>
	<view>
		<view class="box" :style="{width:width}">
			<view id="imgOutLine" :style="{transition:transition,transform:transform}">
				<image :style="{width:width,height:height}" :src="item.src" v-for="(item,index) in imgArray" :key="index"></image>
			</view>
			<view id="headDot" :style="{top:top}">
				<view :class="item.class" :data-id="index" @click="toChange" v-for="(item,index) in dotArray" :key="index"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			imgArray: {
				type: Array,
				default () {
					return []
				}
			},
			width: {
				type: String,
				default: "1000px"
			},
			height: {
				type: String,
				default: "368px"
			},
			top: {
				type: String,
				default: "84.5%"
			},
			second: {
				type: Number,
				default: 5000
			},
			duration: {
				type: Number,
				default: 300
			}
		},
		data() {
			return {
				dotArray: [],
				T: '',
				n: 0,
				a: 0,
				transition: '',
				transform: '',
				length: 0
			}
		},
		onLoad() {

		},
		methods: {
			setTimer(a, n) {
				if (this.T) {
					clearInterval(this.T)
				}
				this.T = setInterval(() => {
					a++
					this.changeClass(a, this.length)
					n += parseInt(this.width)
					this.trans(this.duration, n)
					if (a == this.length) {
						n = 0
						a = 0
						this.changeClass(a, this.length)
						setTimeout(() => {
							this.trans(0, 0)
						}, this.duration)
					}
				}, this.second)
			},
			trans(sec, n) {
				this.transition = sec + "ms"
				this.transform = "translateX(-" + n + "px)"
			},
			toChange(e) {
				let n = e.target.dataset.id
				let a = n
				n = (n * parseInt(this.width))
				this.trans(this.duration, n)
				this.changeClass(a, this.length)
				this.setTimer(a, n)
			},
			changeClass(n, len) {
				for (let i = 0; i < len; i++) {
					if (i == n) {
						this.dotArray[i].class = "currentDot"
					} else {
						this.dotArray[i].class = "dot"
					}
				}

			}
		},
		mounted() {
			let len = this.imgArray.length
			this.length = len
			let item = []
			let arr = []
			for (let i = 0; i < len; i++) {
				if (i == 0) {
					item['index'] = i
					item['class'] = "currentDot"
				} else {
					item['index'] = i
					item['class'] = "dot"
				}
				arr = { ...item
				}
				this.dotArray.push(arr)
			}
			this.imgArray.push(this.imgArray[0])
			this.setTimer(this.a, this.n)
		}
	}
</script>

<style>
	page {
		padding: 0;
		margin: 0;
	}

	.box {
		display: flex;
		height: 368px;
		position: relative;
		overflow: hidden;
		background-color: #007AFF;
	}

	#headDot {
		position: absolute;
		left: 50%;
		top: 84.5%;
		display: flex;
		transform: translateX(-50%);
	}

	.currentDot {
		margin: 0 4px;
		width: 28px;
		height: 8px;
		background: #5e7ce0;
		border-radius: 5px;
		cursor: pointer;
	}

	.dot {
		margin: 0 4px;
		width: 8px;
		height: 8px;
		border-radius: 100%;
		background: #000;
		opacity: .2;
		cursor: pointer;
	}

	#imgOutLine {
		display: flex;
	}
</style>
