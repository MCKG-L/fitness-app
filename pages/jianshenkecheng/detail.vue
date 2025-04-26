
<template>
<view>
<mescroll-uni @init="mescrollInit" :up="upOption" :down="downOption" @down="downCallback" @up="upCallback">
	<view class="content">
		<view class="container" :style='{"minHeight":"100vh","width":"100%","padding":"0","position":"relative","background":"#F4F8FB","height":"auto"}'>
						<swiper :style='{"width":"100%","padding":"20rpx","background":"#fff","height":"360rpx"}' class="swiper" :indicator-dots='true' :autoplay='true' :circular='true' indicator-active-color='#000000' indicator-color='rgba(0, 0, 0, .3)' :duration='600' :interval='6000' :vertical='false'>
				<swiper-item :style='{"width":"100%","overflow":"hidden","borderRadius":"20rpx","background":"#fff","height":"100%"}' v-for="(swiper,index) in swiperList" :key="index">
					<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"100%"}' mode="aspectFill" v-if="swiper.substring(0,4)=='http'" :src="swiper"></image>
					<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"100%"}' mode="aspectFill" v-else :src="baseUrl+swiper"></image>
				</swiper-item>
			</swiper>
												            <view :style='{"width":"100%","padding":"24rpx 0","flexWrap":"wrap","background":"#fff","display":"flex","height":"auto"}' class="detail-content">
				<view :style='{"padding":"0 30rpx","margin":"0 0 10rpx","borderColor":"#ccc","flexWrap":"wrap","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","justifyContent":"space-between","height":"auto"}' class="detail-list-item price">
					<view :style='{"display":"flex","order":"1"}' v-if="storeupFlag==1" @click="shoucang">
						<text class="icon iconfont icon-shoucang12" :style='{"margin":"0 4rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#f59236"}'></text>
						<text :style='{"color":"#f59236","lineHeight":"80rpx","fontSize":"28rpx"}'>取消收藏</text>
					</view>
					<view :style='{"display":"flex","order":"1"}' v-if="storeupFlag==0" @click="shoucang">
						<text class="icon iconfont icon-shoucang11" :style='{"margin":"0 4rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#666"}'></text>
						<text :style='{"color":"#666","lineHeight":"80rpx","fontSize":"28rpx"}'>收藏</text>
					</view>
				</view>

				<view :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="detail-list-item title">
					<view :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}' class="lable">课程名称：</view>
					<view :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}' class="text">{{detail.kechengmingcheng}}</view>
				</view>
				<view :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="detail-list-item title">
					<view :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}' class="lable">健身项目：</view>
					<view :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}' class="text">{{detail.jianshenxiangmu}}</view>
				</view>
				<view :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="detail-list-item title">
					<view :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}' class="lable">目标：</view>
					<view :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}' class="text">{{detail.mubiao}}</view>
				</view>

				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>部位：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.buwei}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>强度：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.qiangdu}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>场地名称：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.changdimingcheng}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>每节价格/元：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.jiage}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>教练工号：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.jiaoliangonghao}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>教练姓名：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.jiaolianxingming}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>点击次数：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.clicknum}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>评论数：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.discussnum}}</view>
				</view>
				<view class="detail-list-item" :style='{"padding":"0 30rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","borderWidth":"0","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
					<view class="lable" :style='{"width":"auto","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#333"}'>收藏数：</view>
					<view  class="text" :style='{"padding":"0px","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)"}'>{{detail.storeupnum}}</view>
				</view>







				<view class="time-content" :style='{"width":"100%","margin":"0 0 24rpx 0","background":"#f4f8fb","height":"auto"}'>
					<view class="comoment-header" :style='{"width":"100%","padding":"10rpx 20rpx","background":"#0060c8","justifyContent":"space-between","display":"flex","height":"auto"}'>
						<view :style='{"padding":"0 24rpx","lineHeight":"80rpx","fontSize":"28rpx","color":"#0060c8","background":"#ffffff","flex":"1"}'>评论</view>
						<view :style='{"border":"10rpx solid #fff","padding":"0 20rpx","background":"#0060c8","display":"flex"}' @click="onCommentTap" class="btn-comment-content" style="display: flex;align-items: center;">
							<view :style='{"margin":"0 8rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#fff"}' class="cuIcon-add"></view>
							<view :style='{"color":"#fff","lineHeight":"80rpx","fontSize":"28rpx"}'>添加评论</view>
						</view>
					</view>
				
					<view :style='{"width":"94%","padding":"24rpx","margin":"24rpx 3% ","background":"#fff","height":"auto"}' v-for="(item,index) in commentList" v-bind:key="index" class="cu-item comment-item">
						<view :style='{"width":"100%","display":"flex","height":"auto"}'>
							<image :style='{"width":"60rpx","margin":"0 8rpx 0 0","borderRadius":"100%","display":"block","height":"60rpx"}' v-if="item.avatarurl" mode="aspectFill" :src="baseUrl+item.avatarurl"></image>
							<view :style='{"color":"#333","lineHeight":"60rpx","fontSize":"28rpx"}' class="text-grey">{{item.nickname}}</view>
						</view>
						<view :style='{"margin":"8rpx 0","lineHeight":"1.5","fontSize":"28rpx","color":"#666"}' class="text-gray text-content text-df">
							<rich-text :nodes="item.content"></rich-text>
						</view>
						<view :style='{"color":"#999","lineHeight":"24rpx","fontSize":"24rpx"}' class="margin-top-sm text-gray text-df">{{item.addtime}}</view>
						<view v-if="item.reply" :style='{"margin":"8rpx 0","lineHeight":"1.5","fontSize":"28rpx","color":"#666"}' class="text-gray text-content text-df">
							回复:<rich-text :nodes="item.reply"></rich-text>
						</view>
						<view style="display: flex;display: flex;justify-content: flex-end;padding: 6rpx 0;" v-if="user&&user.id==item.userid">
							<view style="color: #999;font-size: 16rpx;" @click="delClick(item.id)">删除</view>
						</view>
					</view>
				</view>

				<view class="bottom-content bg-white tabbar border shop" :style='{"width":"100%","padding":"10rpx 24rpx","flexWrap":"wrap","background":"#f4f8fb","display":"flex","height":"auto"}'>

					<button :style='{"border":"0","padding":"0 20rpx","margin":"10rpx","color":"#fff","borderRadius":"8rpx","background":"#afc2f9","width":"auto","fontSize":"28rpx","height":"80rpx"}' v-if="userid&&isAuth('jianshenkecheng','购买课程')" @tap="onAcrossTap('kechengdingdan','','','','')" class="cu-btn bg-brown round shadow-blur" >购买课程</button>
					<button :style='{"border":"0","padding":"0 20rpx","margin":"10rpx","color":"#fff","borderRadius":"8rpx","background":"#afc2f9","width":"auto","fontSize":"28rpx","height":"80rpx"}' v-if="!userid&&isAuthFront('jianshenkecheng','购买课程')" @tap="onAcrossTap('kechengdingdan','','','','')" class="cu-btn bg-brown round shadow-blur" >购买课程</button>
					
				</view>
			</view>
		</view>
	</view>
</mescroll-uni>
</view>
</template>

<script>
	export default {
		data() {
			return {
				btnColor: ['#409eff','#67c23a','#909399','#e6a23c','#f56c6c','#356c6c','#351c6c','#f093a9','#a7c23a','#104eff','#10441f','#a21233','#503319'],
				id: '',
                userid: '',
				detail: {},
				swiperList: [],
				commentList: [],
				mescroll: null, //mescroll实例对象
				downOption: {
					auto: false //是否在初始化后,自动执行下拉回调callback; 默认true
				},
				upOption: {
					noMoreSize: 3, //如果列表已无数据,可设置列表的总数量要大于半页才显示无更多数据;避免列表数据过少(比如只有一条数据),显示无更多数据会不好看; 默认5
					textNoMore: '~ 没有更多了 ~',
				},
				hasNext: true,
				user: {},
				storeupFlag: 0,
				count: 0,
				timer: null,
				title:'',
			}
		},
		components: {
		},
		computed: {
			baseUrl() {
				return this.$base.url;
			},
		},
		async onLoad(options) {
			// #ifdef APP-PLUS
			let page = getCurrentPages()
			this.href = this.baseUrl + 'front/h5/#/' + page[page.length - 1].route
			// #endif
			let table = uni.getStorageSync("nowTable");
			// 获取用户信息
			let res = await this.$api.session(table);
			this.user = res.data;
			this.id = options.id;
            if(options.userid) {
                this.userid = options.userid;
            }
			// 渲染数据
			this.init();
		},
		// #ifdef MP-WEIXIN
		onShareAppMessage(){
			var obj = {
				title: this.title,
				imageUrl: this.swiperList[0]?this.baseUrl + this.swiperList[0]: ''
			}
			return obj
		},
		// #endif
        onUnload() {
            if(this.timer) {
                clearInterval(this.timer);
            }
        },
		async onShow(options) {
			let table = uni.getStorageSync("nowTable");
			// 获取用户信息
			let res = await this.$api.session(table);
			this.user = res.data;
			this.btnColor = this.btnColor.sort(()=> {
				return (0.5-Math.random());
			});
			this.getStoreup();
			let cleanType = uni.getStorageSync('discussjianshenkechengCleanType')
			if(cleanType){
				uni.removeStorageSync('discussjianshenkechengCleanType')
				this.mescroll.num = 1
				this.upCallback(this.mescroll)
				this.init(2);
			}
			let crossCleanType = uni.getStorageSync('crossCleanType')
            if(crossCleanType) {
				uni.removeStorageSync('crossCleanType')
                res = await this.$api.info('jianshenkecheng', this.id);
                this.detail = res.data;
				this.title = this.detail.kechengmingcheng
            }
		},
		destroyed: function() {
			//window.clearInterval(this.inter);
		},
		methods: {
			// 拨打电话
			callClick(row){
				uni.makePhoneCall({
					phoneNumber: row
				})
			},
			// 支付
			onPayTap(){
				if(!this.user){
					return false
				}
				uni.setStorageSync('paytable','jianshenkecheng');
				uni.setStorageSync('payObject',this.detail);
				this.$utils.jump('../pay-confirm/pay-confirm?type=1')
			},
            onDetailTap(item) {
                uni.setStorageSync("useridTag",this.userid);
                this.$utils.jump(`./detail?id=${item.id}&userid=`+this.userid)
            },
			// 收藏
			async getStoreup() {
				if(!this.user){
					return false
				}
				let params = {
					page: 1,
					limit: 1,
					refid : this.id,
					tablename : 'jianshenkecheng',
					userid: this.user.id,
					type: 1,
				}
				let res = await this.$api.list(`storeup`, params);
				this.storeupFlag = res.data.list.length;
			},
			async shoucang(){
				if(!this.user){
					return false
				}
				let _this = this;
				let params = {
					page: 1,
					limit: 1,
					refid : _this.detail.id,
					tablename : 'jianshenkecheng',
					userid: _this.user.id,
					type: 1,
				}
				let res = await _this.$api.list(`storeup`, params);
				if (res.data.list.length == 1) {
					let storeupId = res.data.list[0].id;
					uni.showModal({
						title: '提示',
						content: '是否取消',
						success: async function(res) {
							if (res.confirm) {
								_this.detail.storeupnum--
								await _this.$api.update('jianshenkecheng',_this.detail)
								await _this.$api.del('storeup', JSON.stringify([storeupId]));
								_this.$utils.msg('取消成功');
								_this.getStoreup();
							}
						}
					});
					return;
				}
				uni.showModal({
					title: '提示',
					content: '是否收藏',
					success: async function(res) {
						if (res.confirm) {
							await _this.$api.add('storeup', {
								userid: _this.user.id,
								name: _this.detail.kechengmingcheng,
                                inteltype: _this.detail.jianshenxiangmu,
								picture: _this.swiperList[0],
								refid: _this.detail.id,
								tablename: 'jianshenkecheng',
                                type: 1
							});
							_this.detail.storeupnum++
							await _this.$api.update('jianshenkecheng',_this.detail)
							_this.$utils.msg('收藏成功');
							_this.getStoreup();
						}
					}
				});
			},
			// 跨表
			async onAcrossTap(tableName,crossOptAudit,crossOptPay,statusColumnName,tips,statusColumnValue,type=1){
				if(!this.user){
					return false
				}
				uni.setStorageSync('crossTable','jianshenkecheng');
				uni.setStorageSync(`crossObj`, this.detail);
				uni.setStorageSync(`statusColumnName`, statusColumnName);
				uni.setStorageSync(`statusColumnValue`, statusColumnValue);
				uni.setStorageSync(`tips`, tips);
				if(statusColumnName!=''&&!statusColumnName.startsWith("[")) {
					var obj = uni.getStorageSync('crossObj');
					for (var o in obj){
						if(o==statusColumnName && obj[o]==statusColumnValue){
							this.$utils.msg(tips);
							return
						}
					}
				}
				this.$utils.jump(`../${tableName}/add-or-update?cross=true`);
			},
			// 获取详情
			async init(type=1){
                if(this.timer) {
                    clearInterval(this.timer);
                }
				let res = await this.$api.info('jianshenkecheng', this.id);
				this.detail = res.data;

				this.title = this.detail.kechengmingcheng
				// 轮播图片
				this.swiperList = this.detail.fengmian ? this.detail.fengmian.split(",") : [];
				

				if(type==2){
					this.detail.discussnum++
					await this.$api.update('jianshenkecheng',this.detail)
				}
			},
			// mescroll组件初始化的回调,可获取到mescroll对象
			mescrollInit(mescroll) {
				this.mescroll = mescroll;
			},

			/*下拉刷新的回调 */
			downCallback(mescroll) {
				this.hasNext = true
				mescroll.resetUpScroll()
			},

			/*上拉加载的回调: mescroll携带page的参数, 其中num:当前页 从1开始, size:每页数据条数,默认10 */
			async upCallback(mescroll) {
                let res = await this.$api.list('discussjianshenkecheng', {
					page: mescroll.num,
					limit: 10,
					refid: this.id
				});
				// 如果是第一页数据置空
				if (mescroll.num == 1) this.commentList = [];
				for(let x in res.data.list){
					if(res.data.list[x].content){
						res.data.list[x].content = res.data.list[x].content.replace(/img src/gi,"img style=\"width:100%;\" src")
					}
				}
				this.commentList = this.commentList.concat(res.data.list);
				if (res.data.list.length == 0) this.hasNext = false;
				mescroll.endSuccess(mescroll.size, this.hasNext);

            },



			onChatTap() {
				this.$utils.jump('../chat/chat')
			},
			// 下载
			download(url){
				let _this = this;
				url=_this.$base.url +  url;
				uni.downloadFile({
					url: url,
					success: (res) => {
						if (res.statusCode === 200) {
							_this.$utils.msg('下载成功');
							 window.open(url);
						}
					}
				});
			},
			//
			onCartTabTap() {
				this.$utils.tab('../shop-cart/shop-cart')
			},
			// 添加评论
			async onCommentTap() {
				if(!this.user){
					return false
				}
				this.$utils.jump(`../discussjianshenkecheng/add-or-update?refid=${this.id}`)
			},
			delClick(id){
				let that = this
				uni.showModal({
					title: '提示',
					content: '是否删除此评论？',
					async success(res) {
						if(res.confirm){
							await that.$api.del('discussjianshenkecheng',JSON.stringify([id]))
							that.$utils.msg('删除成功')
							that.detail.discussnum--
							await that.$api.update('jianshenkecheng',that.detail)
							setTimeout(()=>{
								that.upCallback(that.mescroll)
							},1500)
						}
					}
				})
			},
		}
	}
</script>

<style lang="scss">
	page {
	  --animate-duration: 1s;
	  --animate-delay: 1s;
	  --animate-repeat: 1;
	}
	
	.content {
		min-height: calc(100vh - 44px);
		box-sizing: border-box;
	}
	
	.seat-list {
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		background: #FFFFFF;
		margin: 20upx;
		border-radius: 20upx;
		padding: 20upx;
		font-size: 30upx;
		.seat-item {
			width: 33.33%;
			display: flex;
			align-items: center;
			flex-direction: column;
			margin-bottom: 20upx;
	
			.seat-icon {
				width: 50upx;
				height: 50upx;
				margin-bottom: 10upx;
			}
		}
	}
	
	audio {
		display: flex;
		flex-direction: column;
	}
	
	.audio ::v-deep .uni-audio-default {
		width: inherit;
	}
	

</style>
