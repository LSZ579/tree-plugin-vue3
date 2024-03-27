<template>
	<view>
		<button class="btn" @click="toChoose(aprop)" type="primary">多选模式（选择任意一项）</button>
		<button  class="btn" @click="toChoose(bprop)" type="primary">多选模式（关联下级）</button>
		<button class="btn" @click="toChoose(cprop)" type="primary">单选模式(任意一项)</button>
		<button class="btn" @click="toChoose(dprop)" type="primary">单选（只选user）</button>
		<button class="btn" @click="clear()" type="default">清空选择</button>
		<view class="children">
			<view v-for="(item,index) in selectListItem" style="margin: 2px;display: inline-block;font-size: 26rpx;" :key="index">
					<view>名字：{{item.name}};&nbsp;</view>
					路径：
					<view v-for="(row,k) in item.path" style="display: inline-block;font-size: 24rpx;" :key="k">
						{{row.name}}-
					</view>
					<view>--------</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
		data() {
			return {
				selectListItem:[],
				aprop: {
					label: 'name',
					children: 'children',
					multiple:true
				},
				bprop: {
					label: 'name',
					children: 'children',
					multiple:true,
					checkStrictly:true
				},
				cprop: {//单选模式(任意一项)
					label: 'name',
					children: 'children',
					multiple:false,
					nodes:false
				},
				dprop: {//单选模式选user
					label: 'name',
					children: 'children',
					multiple:false,
					nodes:true
				}
			}
		},
		created() {
			uni.$on('selectSuccess',(data)=>{
				this.$set(this,'selectListItem',[...data.list])
			})
		},
		methods: {
			toChoose(prop){
				this.selectListItem = this.selectListItem.map(v=>{
					return {id:v.id}
				})
				// #ifdef H5
					let items = encodeURIComponent(JSON.stringify(this.selectListItem));
				// #endif
				// #ifdef MP-QQ||MP-WEIXIN
					let items = JSON.stringify(this.selectListItem);
				// #endif
				uni.navigateTo({
					url:`../chooseUser/chooseUser?arr=${items}&prop=${JSON.stringify(prop)}`
				})
			},
			clear(){
				this.selectListItem=[];
			}
		}
	}
</script>

<style>
	.children{
		color: #BBB2B2;
	}
	.color{
		color: #bbb2b2;
	}
	.btn{
		margin: 10px auto;
	}
	
</style>
