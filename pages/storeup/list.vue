<template>
<!-- category 2 -->
<mescroll-uni @init="mescrollInit" :up="upOption" :down="downOption" @down="downCallback" @up="upCallback">
	<view class="content">
		<view :style='{"minHeight":"100vh","width":"100%","padding":"0","position":"relative","background":"#F4F8FB","height":"auto"}'>
			<view class="cu-bar bg-white search" :style='{"width":"100%","padding":"20rpx 24rpx","background":"#fff","display":"flex","height":"auto"}'>
				<picker v-if="queryList.length>1" mode="selector" :range="queryList" range-key="queryName" :value="queryIndex" @change="queryChange">
					<view :style='{"width":"40rpx","height":"auto"}'>
						<text class="icon iconfont icon-jiantou18" :style='{"width":"40rpx","fontSize":"40rpx","lineHeight":"80rpx","color":"#666"}'></text>
					</view>
				</picker>
				<view :style='{"margin":"0 12rpx","flex":"1","position":"relative"}' v-if="queryIndex==0" class="search-form round">
					<text class="icon iconfont icon-fangdajing07" :style='{"color":"rgb(153, 153, 153)","left":"0px","textAlign":"center","width":"80rpx","fontSize":"40rpx","lineHeight":"80rpx","position":"absolute","right":"0px"}'></text>
					<input :style='{"border":"0","padding":"12rpx 20rpx 12rpx 80rpx","color":"#333","borderRadius":"20rpx","background":"#FAFAFA","width":"100%","lineHeight":"56rpx","fontSize":"28rpx","height":"80rpx"}' v-model="searchForm.name" type="text" placeholder="名称" ></input>
				</view>
				<button :style='{"border":"0","padding":"0px","margin":"0","color":"#fff","borderRadius":"20rpx","background":"#0060c8","width":"136rpx","lineHeight":"80rpx","fontSize":"28rpx","height":"80rpx"}' @tap="search" class="cu-btn shadow-blur round">搜索</button>
			</view>
			

			<view :style='{"width":"calc(100% - 180rpx)","padding":"16rpx 10rpx","margin":"0 0 20rpx 180rpx","background":"#0060C8","display":"flex"}'>
				<view @click="sortClick('addtime')" :style='{"border":"0","padding":"0 12rpx","margin":"0 8rpx 0 0","outline":"0","borderRadius":"8rpx","background":"#0060c8","display":"flex"}'>
					<text :style='{"color":"#FFFFFF","lineHeight":"48rpx","fontSize":"24rpx"}'>按日期</text>
					<text v-if="listSort!='addtime'" class="icon iconfont icon-shijian18" :style='{"margin":"0 4rpx 0 0","lineHeight":"48rpx","fontSize":"24rpx","color":"#FFFFFF"}'></text>
					<text v-else-if="listSort=='addtime'&&listOrder=='asc'" class="icon iconfont icon-shijian18" :style='{"margin":"0 4rpx 0 0","lineHeight":"48rpx","fontSize":"24rpx","color":"#FFFFFF"}'></text>
					<text v-else-if="listSort=='addtime'&&listOrder=='desc'" class="icon iconfont icon-shijian18" :style='{"margin":"0 4rpx 0 0","lineHeight":"48rpx","fontSize":"24rpx","color":"#FFFFFF"}'></text>
				</view>
			</view>
			<view :style='{"width":"100%","flexWrap":"wrap","display":"flex","height":"auto"}'>
				<view class="uni-product-list" :style='{"padding":"24rpx","margin":"0","flexWrap":"wrap","flex":"1","display":"flex","width":"100%","justifyContent":"space-between","height":"auto"}'>
					<view @tap="onDetailTap(product)" class="uni-product" :style='{"width":"48%","margin":"0 0 20rpx","background":"none","height":"auto"}' v-for="(product,index) in list" :key="index">
						<view class="uni-product-title " :style='{"width":"100%","padding":"4rpx 20rpx","lineHeight":"1.4","fontSize":"28rpx","color":"#333"}'>{{product.name}}</view>
						<image :style='{"width":"100%","padding":"0","margin":"0","objectFit":"cover","display":"block","height":"300rpx"}' mode="aspectFill" class="uni-product-image" v-if="preHttp(product.picture)" :src="product.picture"></image>
						<image :style='{"width":"100%","padding":"0","margin":"0","objectFit":"cover","display":"block","height":"300rpx"}' mode="aspectFill" class="uni-product-image" v-else :src="baseUrl+product.picture"></image>
					</view>
				</view>

			</view>
			
			
			
		</view>

		<button :style='{"border":"0","boxShadow":"0 2rpx 12rpx rgba(0,0,0,.3)","color":"rgb(255, 255, 255)","bottom":"40rpx","right":"8rpx","outline":"none","borderRadius":"100%","background":"rgb(255, 170, 51)","width":"80rpx","lineHeight":"80rpx","fontSize":"28rpx","position":"absolute","height":"80rpx","zIndex":"999"}' v-if="userid && isAuth('storeup','新增')" class="add-btn" @click="onAddTap()">新增</button>
		<button :style='{"border":"0","boxShadow":"0 2rpx 12rpx rgba(0,0,0,.3)","color":"rgb(255, 255, 255)","bottom":"40rpx","right":"8rpx","outline":"none","borderRadius":"100%","background":"rgb(255, 170, 51)","width":"80rpx","lineHeight":"80rpx","fontSize":"28rpx","position":"absolute","height":"80rpx","zIndex":"999"}' v-if="!userid && isAuthFront('storeup','新增')" class="add-btn" @click="onAddTap()">新增</button>
	</view>
</mescroll-uni>
</template>

<script>
	export default {
		data() {
			return {
				leftListList6: [],
				rightListList6: [],
				tempListList6: [],
				leftListNews7: [],
				rightListNews7: [],
				tempListNews7: [],
				btnColor: ['#409eff','#67c23a','#909399','#e6a23c','#f56c6c','#356c6c','#351c6c','#f093a9','#a7c23a','#104eff','#10441f','#a21233','#503319'],
				clicknumColor: ['#409eff','#67c23a','#909399','#e6a23c','#f56c6c','#356c6c','#351c6c','#f093a9','#a7c23a','#104eff','#10441f','#a21233','#503319'],
				queryList:[
					{
						queryName:"名称",
					},
				],
				queryIndex: 0,
				list: [],
				lists: [],
                userid: '',
                type: 1,
				mescroll: null, //mescroll实例对象
				downOption: {
					auto: false //是否在初始化后,自动执行下拉回调callback; 默认true
				},
				upOption: {
					noMoreSize: 5, //如果列表已无数据,可设置列表的总数量要大于半页才显示无更多数据;避免列表数据过少(比如只有一条数据),显示无更多数据会不好看; 默认5
					textNoMore: '~ 没有更多了 ~',
				},
				hasNext: true,
				searchForm:{},
				CustomBar: '0',
				listSort: 'id',
				listOrder: 'desc',
			};
		},
		watch: {
			copyFlowListList6(nVal, oVal) {
				this.tempListList6 = this.cloneData(this.copyFlowListList6);
				this.splitDataList6();
			},
		},
		mounted() {
			this.tempListList6 = this.cloneData(this.copyFlowListList6);
			this.splitDataList6();
		},
		computed: {
			baseUrl() {
				return this.$base.url;
			},
			copyFlowListList6() {
				return this.cloneData(this.list);
			},
			copyFlowListNews7() {
				return this.cloneData(this.list);
			},
		},
		async onShow() {
			this.btnColor = this.btnColor.sort(()=> {
				return (0.5-Math.random());
			});
			this.clicknumColor = this.clicknumColor.sort(()=> {
				return (0.5-Math.random());
			});
			this.hasNext = true
			// 重新加载数据
			if (this.mescroll) this.mescroll.resetUpScroll()
		},
		onLoad(options) {
            if(options.userid) {
                this.userid=options.userid;
            } else {
                this.userid = "";
            }
            if(options.menuJump) {
                this.type=options.menuJump;
            } else {
                this.type = 1;
            }
			this.hasNext = true
			// 重新加载数据
			if (this.mescroll) this.mescroll.resetUpScroll()
		},
		components: {
		},
		methods: {
			async splitDataList6() {
				if (!this.tempListList6.length) return;
				let leftRect = await this.uGetRect('#waterfall-left-column-list-6');
				let rightRect = await this.uGetRect('#waterfall-right-column-list-6');
				// 如果左边小于或等于右边，就添加到左边，否则添加到右边
				let item = this.tempListList6[0];
				// 解决多次快速上拉后，可能数据会乱的问题，因为经过上面的两个await节点查询阻塞一定时间，加上后面的定时器干扰
				// 数组可能变成[]，导致此item值可能为undefined
				if (!item) return;
				
				if (leftRect.height < rightRect.height) {
					this.leftListList6.push(item);
				} else if (leftRect.height > rightRect.height) {
					this.rightListList6.push(item);
				} else {
					// 这里是为了保证第一和第二张添加时，左右都能有内容
					// 因为添加第一张，实际队列的高度可能还是0，这时需要根据队列元素长度判断下一个该放哪边
					if (this.leftListList6.length <= this.rightListList6.length) {
						this.leftListList6.push(item);
					} else {
						this.rightListList6.push(item);
					}
				}
				// 移除临时列表的第一项
				this.tempListList6.splice(0, 1);
				// 如果临时数组还有数据，继续循环
				if (this.tempListList6.length) {
					setTimeout(()=>{
						this.splitDataList6();
					}, 100)
					return
				}
			},
			uGetRect(selector, all) {
				return new Promise(resolve => {
					uni.createSelectorQuery()
					.in(this)
					[all ? 'selectAll' : 'select'](selector)
					.boundingClientRect(rect => {
						if (all && Array.isArray(rect) && rect.length) {
							resolve(rect);
						}
						if (!all && rect) {
							resolve(rect);
						}
					})
					.exec();
				});
			},
			cloneData(data) {
				return JSON.parse(JSON.stringify(data));
			},
			sortClick(type){
				if(this.listSort==type){
					if(this.listOrder == 'desc'){
						this.listOrder = 'asc'
					}else{
						this.listOrder = 'desc'
					}
				}else{
					this.listSort = type
					this.listOrder = 'desc'
				}
				this.search()
			},
            priceChange(price) {
                return Number(price).toFixed(2);
            },
            preHttp(str) {
                return str && str.substr(0,4)=='http';
            },
			//查询条件切换
			queryChange(e) {
				this.queryIndex=e.detail.value;
				this.searchForm.name="";
			},
			//类别搜索
			// mescroll组件初始化的回调,可获取到mescroll对象
			mescrollInit(mescroll) {
				this.mescroll = mescroll;
			},
			/*下拉刷新的回调 */
			downCallback(mescroll) {
				this.hasNext = true
				// 重置分页参数页数为1
				mescroll.resetUpScroll()
			},
			/*上拉加载的回调: mescroll携带page的参数, 其中num:当前页 从1开始, size:每页数据条数,默认10 */
			async upCallback(mescroll) {
				let params = {
					page: mescroll.num,
					limit: mescroll.size
				}
				params['sort'] = this.listSort;
				params['order'] = this.listOrder;

				if(this.searchForm.name){
					params['name'] = '%' + this.searchForm.name + '%'
				}
				params['type']=this.type;
                let res = {}
                if(this.userid) {
                    res = await this.$api.page(`storeup`, params);
                } else {
                    res = await this.$api.list(`storeup`, params);
                }
				// 如果是第一页数据置空
				if (mescroll.num == 1) this.list = [];
				
				this.list = this.list.concat(res.data.list);
				let length = Math.ceil(this.list.length/6)
				let arr = [];
				for (let i = 0; i<length; i++){
					arr[i] = this.list.slice(i*6, (i+1)*6)
				}
				this.lists = arr
				if (res.data.list.length == 0) this.hasNext = false;
				mescroll.endSuccess(mescroll.size, this.hasNext);
				this.tempListList6 = this.copyFlowListList6;
				this.splitDataList6();
			},
			// 详情
			onDetailTap(item) {
				this.$utils.jump(`../${item.tablename}/detail?id=${item.refid}`)
			},
			onUpdate(e){
				this.onUpdateTap(e.currentTarget.dataset.row)
			},
			// 修改
			onUpdateTap(row){
                uni.setStorageSync("useridTag",this.userid);
				this.$utils.jump(`./add-or-update?id=${row.id}`)
			},
			// 添加
			onAddTap(){
                uni.setStorageSync("useridTag",this.userid);
				this.$utils.jump(`./add-or-update`)
			},
			onDelete(e){
				this.onDeleteTap(e.currentTarget.dataset.row.id)
			},
			onDeleteTap(id){
				var _this = this;
				uni.showModal({
					title: '提示',
					content: '是否确认删除',
					success: async function(res) {
						if (res.confirm) {
							await _this.$api.del('storeup', JSON.stringify([id]));
							_this.hasNext = true
							// 重置分页参数页数为1
							_this.search()
						}
					}
				});
			},
			// 搜索
			async search(){
				this.mescroll.num = 1
				let searchForm = {
					page: this.mescroll.num,
					limit: this.mescroll.size
				}
				searchForm['sort'] = this.listSort;
				searchForm['order'] = this.listOrder;

				if(this.searchForm.name){
					searchForm['name'] = '%' + this.searchForm.name + '%'
				}
				searchForm['type']=this.type;
                let res = {};
                if(this.userid) {
                    res = await this.$api.page(`storeup`, searchForm);
                } else {
                    res = await this.$api.list(`storeup`, searchForm);
                }
				// 如果是第一页数据置空
				if (this.mescroll.num == 1) this.list = [];
				this.list = this.list.concat(res.data.list);
				let length = Math.ceil(this.list.length/6)
				let arr = [];
				for (let i = 0; i<length; i++){
					arr[i] = this.list.slice(i*6, (i+1)*6)
				}
				this.lists = arr
				if (res.data.list.length == 0) this.hasNext = false;
				this.mescroll.endSuccess(this.mescroll.size, this.hasNext);
			}
		}
	};
</script>

<style lang="scss" scoped>
	.content {
		min-height: calc(100vh - 44px);
		box-sizing: border-box;
	}
	
	.category-one .tab {
		cursor: pointer;
		padding: 0 20rpx;
		color: #fff;
		background: red;
		display: inline-block;
		width: auto;
		font-size: 28rpx;
		line-height: 80rpx;
	}
	
	.category-one .tab.active {
		cursor: pointer;
		padding: 0 20rpx;
		color: #fff;
		background: #000;
		display: inline-block;
		width: auto;
		font-size: 28rpx;
		line-height: 80rpx;
	}
	
	.category-two .tab {
		cursor: pointer;
		border-radius: 0 20rpx 20rpx 0;
		padding: 0;
		margin: 10rpx 0;
		color: #595959;
		background: #fff;
		display: inline-block;
		width: 100%;
		font-size: 28rpx;
		line-height: 80rpx;
		text-align: center;
	}
	
	.category-two .tab.active {
		cursor: pointer;
		border-radius: 0 20rpx 20rpx 0;
		padding: 0;
		color: #fff;
		background: #0060C8;
		display: inline-block;
		width: 100%;
		font-size: 28rpx;
		line-height: 80rpx;
		text-align: center;
	}
	
	.category-three .tab {
		cursor: pointer;
		padding: 0;
		color: #fff;
		background: burlywood;
		display: inline-block;
		width: 100%;
		font-size: 28rpx;
		line-height: 80rpx;
		text-align: center;
	}
	
	.category-three .tab.active {
		cursor: pointer;
		padding: 0;
		color: #fff;
		background: #000;
		display: inline-block;
		width: 100%;
		font-size: 28rpx;
		line-height: 80rpx;
		text-align: center;
	}
</style>
