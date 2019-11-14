<template>
	<view>
		<uni-drawer :visible="showRigth" mode="right" @close="closeDrawer('right')">
			<!-- #ifndef MP-BAIDU || MP-ALIPAY || MP-TOUTIAO -->
			<uni-list>
				<uni-list-item title="Item1" />
				<uni-list-item title="Item2" />
				<uni-list-item :show-badge="true" title="Item3" badge-text="12" />
			</uni-list>
			<!-- #endif -->
			<!-- #ifdef MP-BAIDU || MP-ALIPAY || MP-TOUTIAO -->
			<view class="uni-list">
				<uni-list-item title="Item1" />
				<uni-list-item title="Item2" />
				<uni-list-item :show-badge="true" title="Item3" badge-text="12" />
			</view>
			<!-- #endif -->
		</uni-drawer>
	</view>
</template>

<script>
	import uniDrawer from '@/components/uni-drawer/uni-drawer.vue'
	import uniList from '@/components/uni-list/uni-list.vue'
	import uniListItem from '@/components/uni-list-item/uni-list-item.vue'
	export default {
		components:{
			uniDrawer,
			uniList,
			uniListItem
		},
		methods:{
			hide() {
				this.showRigth = false
			},
			closeDrawer(e) {
				this.showRigth = false
			},
			onNavigationBarButtonTap(e) {
				this.showRigth = !this.showRigth
			},
			onBackPress() {
				if (this.showRigth || this.showLeft) {
					this.hide()
					return true
				}
			}
		},
		data() {
			return {
				showRigth: false,
				showLeft: false
			}
		}
	}
</script>

<style lang="less">

</style>
