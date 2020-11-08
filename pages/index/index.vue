<template>
	<view>
		<carousel :top="top" :second="second" :imgArray="imgArray" :width="width"></carousel>
	</view>
</template>

<script>
	import carousel from "../../componemts/czx-carousel/czx-carousel.vue"
	export default {
		components: {
			carousel
		},
		data() {
			return {
				imgArray: [{
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-1.fdbf82d4c2ca7fad3225.jpg",
				}, {
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-2.64b1407e7a8db89d6cf2.jpg",
				}, {
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-3.ce76c93c7a8a149ce2a2.jpg",
				}, {
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-4.4ac0f6534a11844638e4.jpg",
				}, {
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-5.0e9bb68d425a4a5c3b18.jpg",
				}, {
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-6.80cafe61bcb20a98eb1e.jpg",
				}, {
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-7.d315f5241113c1fd9035.jpg",
				}, {
					src: "https://res.devcloud.huaweicloud.com/obsdevui/diploma/8.1.17.002/banner-8.d14241daf518717981c6.jpg",
				}],
				width: "800px",
				second: 1000,
				top: "84.5%"
			}
		},
		methods: {

		},
		onShow: function() {
			uni.getSystemInfo({
				complete: e => {
					this.width = e.windowWidth + "px"
					console.log(e)
				}
			})
		}
	}
</script>

<style>
</style>
