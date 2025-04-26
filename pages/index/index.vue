<template>
<view class="content">
	<view :style='{"width":"100%","padding":"40rpx 40rpx 100rpx","background":"#F4F8FB","height":"100%"}'>
		<swiper :style='{"width":"100%","borderRadius":"40rpx","background":"#fff","height":"360rpx"}' class="swiper" :indicator-dots='true' :autoplay='true' :circular='true' indicator-active-color='#000000' indicator-color='rgba(0, 0, 0, .3)' :duration='600' :interval='9000' :vertical='false'>
			<swiper-item :style='{"width":"100%","borderRadius":"40rpx","background":"#fff","height":"360rpx"}' v-for="(swiper,index) in swiperList" :key="index" @tap="onSwiperTap(swiper)">
				<image :style='{"width":"100%","objectFit":"cover","borderRadius":"40rpx","display":"block","height":"360rpx"}' mode="aspectFill" :src="baseUrl+swiper.img"></image>
				<view v-if="false" :style='{"width":"100%","padding":"0 8rpx","lineHeight":"60rpx","fontSize":"28rpx","color":"#333","background":"#fff"}'>{{ swiper.title }}</view>
			</swiper-item>
		</swiper>
		<!-- menu -->
		<view v-if="true" class="menu" :style='{"width":"100%","padding":"0","margin":"0","flexWrap":"wrap","display":"flex","height":"auto"}'>
            <block v-for="(item,index1) in menuList" v-bind:key="item.roleName">
                <block v-if="index1==0" v-bind:key="index" v-for=" (menu,index) in item.frontMenu">
                    <block v-bind:key="sort" v-for=" (child,sort) in menu.child">
                        <block v-bind:key="sort2" v-for=" (button,sort2) in child.buttons">
                            <view :style='{"width":"23%","padding":"12rpx 0","margin":"10rpx 1%","height":"auto"}' class="menu-list" v-if="button=='查看' && child.tableName!='yifahuodingdan' && child.tableName!='yituikuandingdan' &&child.tableName!='yiquxiaodingdan' && child.tableName!='weizhifudingdan' && child.tableName!='yizhifudingdan' && child.tableName!='yiwanchengdingdan' " @tap="onPageTap2('../'+child.tableName+'/list')">
                                <view class="iconarr" :class="child.appFrontIcon" :style='{"margin":"0px auto","color":"#333","borderRadius":"100%","display":"block","width":"80rpx","lineHeight":"80rpx","fontSize":"80rpx","height":"80rpx"}'></view>
                                <view :style='{"padding":"0","margin":"12rpx auto 0","color":"#333","textAlign":"center","width":"100%","lineHeight":"28rpx","fontSize":"28rpx"}'>{{child.menu.split("列表")[0]}}</view>
                            </view>
                        </block>
                    </block>
                </block>
            </block>
		</view>
		<!-- menu -->
		<!-- 系统简介 -->
		<view :style='{"padding":"10rpx 24rpx","margin":"0 0 20rpx","borderRadius":"40rpx","flexWrap":"wrap","backgroundImage":"url(http://codegen.caihongy.cn/20231206/383b80f5364249fd9081c8fd776f01e8.png)","display":"flex","width":"100%","backgroundSize":"100% 100%","height":"360rpx"}'>
			<view :style='{"width":"100%","lineHeight":"60rpx","fontSize":"48rpx","overflow":"hidden","color":"#576382","height":"60rpx"}'>{{systemIntroductionDetail.title}}</view>
			<view :style='{"margin":"0 0 20rpx","overflow":"hidden","color":"#818AB1","width":"100%","lineHeight":"60rpx","fontSize":"32rpx","height":"60rpx"}'>{{systemIntroductionDetail.subtitle}}</view>
			<view :style='{"width":"100%","padding":"0 10rpx","flexWrap":"wrap","display":"none","height":"auto"}'>
				<img :style='{"margin":"0 10rpx","objectFit":"cover","flex":1,"display":"block","height":"160rpx"}' v-if="systemIntroductionDetail.picture1" :src="baseUrl+systemIntroductionDetail.picture1">
				<img :style='{"margin":"0 10rpx","objectFit":"cover","flex":1,"display":"block","height":"160rpx"}' v-if="systemIntroductionDetail.picture2" :src="baseUrl+systemIntroductionDetail.picture2">
				<img :style='{"margin":"0 10rpx","objectFit":"cover","flex":1,"display":"block","height":"160rpx"}' v-if="systemIntroductionDetail.picture3" :src="baseUrl+systemIntroductionDetail.picture3">
			</view>
			<view :style='{"padding":"0","margin":"0 0 20rpx 0","overflow":"hidden","color":"rgb(102, 102, 102)","width":"100%","fontSize":"28rpx","height":"190rpx"}' v-html="systemIntroductionDetail.content"></view>
			<view :style='{"border":"0","padding":"0 30rpx","margin":"0 auto","textAlign":"center","background":"#409EFF","display":"none","width":"auto","lineHeight":"56rpx"}'>
			  <text :style='{"color":"#f5f5f5","fontSize":"24rpx"}'>更多</text>
			  <text class="icon iconfont icon-gengduo1" :style='{"color":"#f5f5f5","fontSize":"24rpx"}'></text>
			</view>
			<view :style='{"width":"50%","background":"url(http://codegen.caihongy.cn/20201114/7856ba26477849ea828f481fa2773a95.jpg) 0% 0% / cover no-repeat","display":"none","height":"160rpx"}' />
			<view :style='{"width":"50%","background":"url(http://codegen.caihongy.cn/20201114/7856ba26477849ea828f481fa2773a95.jpg) 0% 0% / cover no-repeat","display":"none","height":"160rpx"}' />
		</view>
		<!-- 商品推荐 -->
		<view class="listBox recommend" :style='{"margin":"0 0 20rpx"}'>
			<view class="title" :style='{"width":"100%","padding":"0 24rpx","margin":"0"}'>
				<view :style='{"color":"#0060C8","fontSize":"48rpx","lineHeight":"88rpx"}'>健身课程推荐</view>
			</view>
			<!-- 样式2 -->
			<view class="list-box style2" :style='{"width":"100%","padding":"24rpx","height":"auto"}'>
			  <view class="tabView" :style='{"width":"100%","flexWrap":"wrap","display":"flex"}'>
			    <view class="tab" :class="jianshenkechengIndex2 == index ?'tabActive':''" v-for="(item,index) in jianshenkechengCateList2" :key="index" @click="recommendTabClick2(index,'jianshenkecheng')">
			      <text class="icon iconfont icon-zhankai19" :style='{"margin":"0 4rpx 0 0","lineHeight":"68rpx","fontSize":"24rpx","color":"inherit"}'></text>
			      <text :style='{"color":"inherit","lineHeight":"68rpx","fontSize":"28rpx"}'>{{item.jianshenxiangmu}}</text>
			    </view>
			  </view>
			  <view :style='{"padding":"24rpx 0","margin":"0","flexWrap":"wrap","display":"flex","width":"100%","justifyContent":"space-between","height":"auto"}'>
			    <view @tap="onDetailTap('jianshenkecheng',product.id)" v-for="(product,index) in jianshenkechenglist" :key="index" class="list-item" :style='{"boxShadow":"0 2rpx 2rpx rgba(0,0,0,.3)","margin":"0 0 20rpx","backgroundColor":"#fff","overflow":"hidden","borderRadius":"20rpx 20rpx 0 0","flexWrap":"wrap","display":"flex","width":"48%","position":"relative","justifyContent":"space-around","height":"auto"}'>
					<view :style='{"width":"100%","padding":"4rpx 20rpx","lineHeight":"40rpx","fontSize":"28rpx","color":"#333","order":"1"}' class="list-item-title ">课程名称:{{product.kechengmingcheng}}</view>
					<image :style='{"width":"100%","padding":"0","margin":"0","objectFit":"cover","display":"block","height":"240rpx"}' class="list-item-image" mode="aspectFill" v-if="product.fengmian.substring(0,4)=='http'" :src="product.fengmian"></image>
					<image :style='{"width":"100%","padding":"0","margin":"0","objectFit":"cover","display":"block","height":"240rpx"}' class="list-item-image" mode="aspectFill" v-else :src="product.fengmian?baseUrl+product.fengmian.split(',')[0]:''"></image>
					<view :style='{"width":"100%","padding":"4rpx 20rpx","lineHeight":"40rpx","fontSize":"28rpx","color":"#333","order":"1"}' class="list-item-title ">{{product.jianshenxiangmu}}</view>
					<view :style='{"width":"100%","padding":"4rpx 20rpx","lineHeight":"40rpx","fontSize":"28rpx","color":"#333","order":"1"}' class="list-item-title ">{{product.mubiao}}</view>
				  <view :style='{"padding":"0 20rpx","display":"none"}'>
			        <text class="icon iconfont icon-shijian21" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#666"}'></text>
			        <text :style='{"color":"#666","lineHeight":"1.5","fontSize":"24rpx"}'>{{product.addtime}}</text>
			      </view>
			      <view :style='{"padding":"0 20rpx","display":"none"}'>
			        <text class="icon iconfont icon-geren16" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#666"}'></text>
			        <text :style='{"color":"#666","lineHeight":"1.5","fontSize":"24rpx"}'>{{product.jiaoliangonghao}}</text>
			      </view>
			      <view :style='{"width":"30%","padding":"0 10rpx","order":"3"}'>
			        <text class="icon iconfont icon-shoucang10" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#666"}'></text>
			        <text :style='{"color":"#666","lineHeight":"1.5","fontSize":"24rpx"}'>{{product.storeupnum}}</text>
			      </view>
			      <view :style='{"width":"30%","padding":"0 10rpx","order":"4"}'>
			        <text class="icon iconfont icon-chakan9" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#666"}'></text>
			        <text :style='{"color":"#666","lineHeight":"1.5","fontSize":"24rpx"}'>{{product.clicknum}}</text>
			      </view>
			    </view>
			  </view>
			</view>
		</view>
		<!-- 商品推荐 -->
		
		<!-- 商品列表 -->
		<!-- 商品列表 -->
		<!-- 新闻资讯 -->
		<view class="listBox news" :style='{"margin":"0 0 20rpx","background":"#fff"}'>
			<view class="title" :style='{"width":"100%","padding":"0 24rpx","margin":"0","justifyContent":"space-between","display":"flex"}'>
				<view :style='{"color":"#0060C8","fontSize":"48rpx","lineHeight":"88rpx"}'>健身知识</view>
				<view :style='{"alignItems":"center","justifyContent":"center","display":"flex"}' @tap="onPageTap('news')">
				  <text :style='{"color":"#AAAAAA","fontSize":"28rpx"}'>更多</text>
				  <text class="icon iconfont icon-gengduo1" :style='{"color":"#AAAAAA","fontSize":"28rpx"}'></text>
				</view>
			</view>
		  <!-- 样式4 -->
		  <view class="news-box1" :style='{"width":"100%","padding":"24rpx","margin":"0","height":"auto"}'>
			<view @tap="onNewsDetailTap(item.id)" v-for="(item,index) in news" :key="index" class="list-item" :style='{"boxShadow":"0 0px 10rpx rgba(0,0,0,.3)","padding":"10rpx","margin":"0 0 30rpx","borderRadius":"20rpx","flexWrap":"wrap","display":"flex","width":"100%","height":"auto"}'>
			  <view class="list-item-body" :style='{"padding":"0","margin":"0","flexWrap":"wrap","display":"flex","width":"calc(100% - 200rpx)","justifyContent":"space-around","height":"auto"}'>
				<view :style='{"padding":"0 20rpx","margin":"0","overflow":"hidden","color":"#000","width":"100%","lineHeight":"50rpx","fontSize":"28rpx","height":"50rpx"}' class="title ">{{item.title}}</view>
				<view :style='{"padding":"0 20rpx","margin":"0","overflow":"hidden","color":"#666","width":"100%","lineHeight":"40rpx","fontSize":"28rpx","height":"40rpx"}' class="text">{{item.introduction}}</view>
			    <view :style='{"padding":"0 20rpx","display":"none"}'>
			      <text class="icon iconfont icon-shijian21" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#666"}'></text>
			      <text :style='{"color":"#666","lineHeight":"1.5","fontSize":"24rpx"}'>{{item.addtime}}</text>
			    </view>
			    <view :style='{"width":"100%","padding":"4rpx 20rpx"}'>
			      <text class="icon iconfont icon-geren16" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#666"}'></text>
			      <text :style='{"color":"#666","lineHeight":"1.5","fontSize":"24rpx"}'>{{item.name}}</text>
			    </view>
			    <view :style='{"padding":"0 16rpx","background":"#C6E0F9","display":"inline-block"}'>
			      <text class="icon iconfont icon-zan10" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#6991BC"}'></text>
			      <text :style='{"color":"#6991BC","lineHeight":"1.5","fontSize":"24rpx"}'>{{item.thumbsupnum}}</text>
			    </view>
			    <view :style='{"padding":"0 16rpx","background":"#C6E0F9","display":"inline-block"}'>
			      <text class="icon iconfont icon-shoucang10" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#6991BC"}'></text>
			      <text :style='{"color":"#6991BC","lineHeight":"1.5","fontSize":"24rpx"}'>{{item.storeupnum}}</text>
			    </view>
			    <view :style='{"padding":"0 16rpx","background":"#C6E0F9","display":"inline-block"}'>
			      <text class="icon iconfont icon-chakan9" :style='{"margin":"0 4rpx 0 0","lineHeight":"1.5","fontSize":"24rpx","color":"#6991BC"}'></text>
			      <text :style='{"color":"#6991BC","lineHeight":"1.5","fontSize":"24rpx"}'>{{item.clicknum}}</text>
			    </view>
			  </view>
			  <image :style='{"width":"200rpx","objectFit":"cover","borderRadius":"20rpx","display":"block","height":"200rpx"}' mode="aspectFill" class="listmpic" :src="baseUrl+item.picture"></image>
			</view>
		  </view>
		</view>
		<!-- 新闻资讯 -->
	</view>
</view>
</template>

<script>
    import menu from '@/utils/menu'
	import '@/assets/css/global-restaurant.css'
	import uniIcons from "@/components/uni-ui/lib/uni-icons/uni-icons.vue"
	export default {
		components: {
			uniIcons
		},
		data() {
			return {
				options2: {
					effect: 'flip',
					loop : true
				},
				options3: {
					effect: 'cube',
					loop : true,
					cubeEffect: {
						shadow: true,
						slideShadows: true,
						shadowOffset: 20,
						shadowScale: 0.94,
					}
				},
				rows: 2,
				column: 4,
				iconArr: [
				  'cuIcon-same',
				  'cuIcon-deliver',
				  'cuIcon-evaluate',
				  'cuIcon-shop',
				  'cuIcon-ticket',
				  'cuIcon-cascades',
				  'cuIcon-discover',
				  'cuIcon-question',
				  'cuIcon-pic',
				  'cuIcon-filter',
				  'cuIcon-footprint',
				  'cuIcon-pulldown',
				  'cuIcon-pullup',
				  'cuIcon-moreandroid',
				  'cuIcon-refund',
				  'cuIcon-qrcode',
				  'cuIcon-remind',
				  'cuIcon-profile',
				  'cuIcon-home',
				  'cuIcon-message',
				  'cuIcon-link',
				  'cuIcon-lock',
				  'cuIcon-unlock',
				  'cuIcon-vip',
				  'cuIcon-weibo',
				  'cuIcon-activity',
				  'cuIcon-friendadd',
				  'cuIcon-friendfamous',
				  'cuIcon-friend',
				  'cuIcon-goods',
				  'cuIcon-selection'
				],
                role : '',
                systemIntroductionDetail: {},
                menuList: [],
                swiperMenuList:[],
                user: {},
                tableName:'',

				//轮播
				swiperList: [],
				jianshenkechengIndex2: 0,
				jianshenkechengCateList2: [],
				jianshenkechenglist: [],
				news: [],
			}
		},
		watch: {
		},
		mounted() {
		},
		computed: {
			baseUrl() {
				return this.$base.url;
			},
		},
        async onLoad(){
            this.role = uni.getStorageSync("appRole");
            let table = uni.getStorageSync("nowTable");
            let res = await this.$api.session(table);
            this.user = res.data;
            this.tableName = table;
            let menus = menu.list();
            this.menuList = menus;
            this.menuList.forEach((item,key) => {
                if(key==0) {
                    item.frontMenu.forEach((item2,key2) => {
                        if(item2.child[0].buttons.indexOf("查看")>-1) {
                            this.swiperMenuList.push(item2);
                        }
                    })
                }
            })
        },
		async onShow() {
            let res;
			// 轮播图
			let swiperList = []
			res = await this.$api.list('config', {
				page: 1,
				limit: 5
			});
			for (let item of res.data.list) {
				if (item.name.indexOf('picture') >= 0 && item.value && item.value!="" && item.value!=null ) {
					swiperList.push({
						img: item.value,
                        title: item.name,
						url: item.url
					});
				}
			}
			if (swiperList) {
				this.swiperList = swiperList;
			}
			

            this.getSystemIntroduction();
			// 推荐信息
			if(uni.getStorageSync("appUserid")) {
			    res = await this.$api.page('jianshenxiangmu', {page:1,limit:100});
			} else {
			    res = await this.$api.list('jianshenxiangmu', {page:1,limit:100});
			}
			res.data.list.splice(0,0,{id:0,jianshenxiangmu:'全部'})
			this.jianshenkechengIndex2 = 0
			this.jianshenkechengCateList2 = res.data.list
			this.getRecommendList()
			this.getHomeList()
			this.getNewsList()
		},
		methods: {
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
			newsTabClick2(index){
				this.newsIndex2 = index
				this.getNewsList()
			},
			async getNewsList(){
				let res;
				let params = {
					page: 1,
					limit: 6,
					sort: 'id',
					order: 'desc',
				}
				// 健身知识
				res = await this.$api.list('news', params)
				this.news = res.data.list
			},
			homeTabClick2(index,name){
				this['home' + name + 'Index2'] = index
				this.getHomeList()
			},
			async getHomeList(){
				let res;
				let params;
			},
			recommendTabClick2(index,name){
				this[name + 'Index2'] = index
				this.getRecommendList()
			},
			async getRecommendList(){
				let res;
				let params;
				// 推荐信息
				params = {
					page: 1,
					limit: 6,
				}
				if(this.jianshenkechengIndex2){
					params.jianshenxiangmu = this.jianshenkechengCateList2[this.jianshenkechengIndex2].jianshenxiangmu
				}
				if(uni.getStorageSync("appUserid")) {
					res = await this.$api.recommend2('jianshenkecheng', params);
				} else {
					res = await this.$api.recommend('jianshenkecheng', params);
				}
				this.jianshenkechenglist = res.data.list
				

			},
			//轮播图跳转
			onSwiperTap(e) {
				if(e.url) {
					if (e.url.indexOf('https') != -1) {
						window.open(e.url)
					} else {
						this.$utils.jump(e.url)
					}
				}
			},
            async getSystemIntroduction() {
                let res = await this.$api.info('systemintro', 1)
                this.systemIntroductionDetail = res.data;
            },
			// 新闻详情
			onNewsDetailTap(id) {
				this.$utils.jump(`../news-detail/news-detail?id=${id}`)
			},
			// 推荐列表点击详情
			onDetailTap(tableName, id) {
				this.$utils.jump(`../${tableName}/detail?id=${id}`)
			},
			onPageTap(tableName){

				uni.navigateTo({
					url: `../${tableName}/list`,
					fail: function(){
						uni.switchTab({
							url: `../${tableName}/list`
						});
					}
				});
				// this.$utils.jump(`../${tableName}/list`)
			},
            onPageTap2(url) {
                uni.setStorageSync("useridTag",0);
                uni.navigateTo({
                    url: url,
                    fail: function() {
                        uni.switchTab({
                            url: url
                        });
                    }
                });
            }
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		min-height: calc(100vh - 44px);
		box-sizing: border-box;
	}
	.recommend {
		.style2 {
			.tabView {
				.tab {
					border: 0px solid rgb(64, 158, 255);
					border-radius: 40rpx;
					padding: 0 10rpx;
					margin: 0 10rpx;
					color: #AAAAAA;
				}
				.tabActive {
					border: 0px solid rgb(64, 158, 255);
					border-radius: 40rpx;
					padding: 0 10rpx;
					margin: 0 10rpx;
					color: #000000;
				}
			}
		}
	}

</style>
