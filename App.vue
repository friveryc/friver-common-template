<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/* 引入uView基础样式 */
	@import "@/uni_modules/uview-ui/index.scss";

	/* 引入tmUI: */
	@import "@/uni_modules/tm-vuetify/mian.min.css";
	/* 主题包 */
	@import "@/uni_modules/tm-vuetify/scss/theme.css";

	/* 引入colorUI样式*/
	@import "colorui/main.css";
	@import "colorui/icon.css";

	/*每个页面公共css */
</style>
