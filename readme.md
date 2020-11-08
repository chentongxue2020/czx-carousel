# czx-carousel轮播图
基于uniapp开发的通用组件
# 下载地址
- [dcloud插件市场：https://ext.dcloud.net.cn/plugin?id=3393](https://ext.dcloud.net.cn/plugin?id=3393)

- [github地址：https://github.com/chentongxue2020/czx-carousel.git](https://github.com/chentongxue2020/czx-carousel.git)
# 使用方式
在 script 中引用组件
```
import carousel from "../../components/czx-carousel/czx-carousel.vue"
	export default {
		components: {
			carousel
		}
    }
```
在 template 中使用组件
```
<carousel :top="top" :second="second" :imgArray="imgArray" :width="width" ></carousel>
```
# 属性说明

| 属性 | 类型 | 默认值 | 必需 | 说明 |
| :----: | :----: | :----: | :----: | :----: |
| imgArray | Array | 空 | 是 | 轮播图是轮播图片 |
| width | String | 1000px | 是，如果未传，则使用默认值 | 轮播图的宽度，如：宽为1000，则width为1000px，需带上“px” |
| height | String | 368px | 是，如果未传，则使用默认值  | 轮播图的高度，如：高为368，则height为368px，需带上“px” |
| top | String | 84.5% | 是，如果未传，则使用默认值  | dot点的顶部距离轮播图顶部的距离所占的比例，如：所占的比例为84.5%，则top为84.5%，需带上“%” |
| second | Number | 5000 | 是，如果未传，则使用默认值  | 轮播图每换一张图片相隔的时间，单位为毫秒，如：5秒，则将值设为5000即可 |
| duration | Number | 300 | 是，如果未传，则使用默认值  | 轮播图每一张图片的转换过渡时间，单位为毫秒，如：0.3秒，则将值设为300即可 |

# 使用样例
```
<template>
	<view>
		<carousel :top="top" :second="second" :imgArray="imgArray" :width="width"></carousel>
	</view>
</template>

<script>
	import carousel from "../../components/czx-carousel/czx-carousel.vue" //引入
	export default {
		components: {
			carousel  //注册
		},
		data() {
			return {
				imgArray: [{
					src: "./demo1.jpg",  //轮播图图片链接地址，这里仅是示例
				}, {
					src: "./demo2.jpg",  //轮播图图片链接地址，这里仅是示例
				}, {
					src: "./demo3.jpg",  //轮播图图片链接地址，这里仅是示例
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

```

