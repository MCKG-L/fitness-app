<template>
<view class="content">
	<view :style='{"minHeight":"100vh","width":"100%","padding":"20rpx 40rpx","position":"relative","background":"#edeff3","height":"auto"}'>
		<form :style='{"width":"100%","padding":"24rpx","background":"#edeff3","display":"block","height":"auto"}' class="app-update-pv">
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">课程名称</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.kechengmingcheng" v-model="ruleForm.kechengmingcheng" placeholder="课程名称"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="" @tap="fengmianTap">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">封面</view>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' class="avator" v-if="ruleForm.fengmian" :src="baseUrl+ruleForm.fengmian.split(',')[0]" mode="aspectFill"></image>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' class="avator" v-else src="../../static/gen/upload.png" mode="aspectFill"></image>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class=" select">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">健身项目</view>
				<picker :disabled="ro.jianshenxiangmu" :style='{"width":"100%","flex":"1","height":"auto"}' @change="jianshenxiangmuChange" :value="jianshenxiangmuIndex" :range="jianshenxiangmuOptions">
					<view :style='{"width":"100%","lineHeight":"80rpx","fontSize":"28rpx","color":"#000000"}' class="uni-input">{{ruleForm.jianshenxiangmu?ruleForm.jianshenxiangmu:"请选择健身项目"}}</view>
				</picker>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">目标</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.mubiao" v-model="ruleForm.mubiao" placeholder="目标"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">部位</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.buwei" v-model="ruleForm.buwei" placeholder="部位"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class=" select">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">强度</view>
				<picker :disabled="ro.qiangdu" :style='{"width":"100%","flex":"1","height":"auto"}' @change="qiangduChange" :value="qiangduIndex" :range="qiangduOptions">
					<view :style='{"width":"100%","lineHeight":"80rpx","fontSize":"28rpx","color":"#000000"}' class="uni-input">{{ruleForm.qiangdu?ruleForm.qiangdu:"请选择强度"}}</view>
				</picker>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">场地名称</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.changdimingcheng" v-model="ruleForm.changdimingcheng" placeholder="场地名称"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">每节价格/元</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.jiage" v-model="ruleForm.jiage" placeholder="每节价格/元" type="number"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class=" select">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">教练工号</view>
				<picker :disabled="ro.jiaoliangonghao" :style='{"width":"100%","flex":"1","height":"auto"}' @change="jiaoliangonghaoChange" :value="jiaoliangonghaoIndex" :range="jiaoliangonghaoOptions">
					<view :style='{"width":"100%","lineHeight":"80rpx","fontSize":"28rpx","color":"#000000"}' class="uni-input">{{jiaoliangonghaoOptions[jiaoliangonghaoIndex]}}</view>
				</picker>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">教练姓名</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' disabled v-model="ruleForm.jiaolianxingming" placeholder="教练姓名"></input>
			</view>
 

			
			<view :style='{"width":"100%","justifyContent":"space-between","display":"flex","height":"auto"}' class="btn" >
				<button :style='{"border":"0","padding":"0px","margin":"0","color":"rgb(255, 255, 255)","borderRadius":"60rpx","background":"#0060c8","width":"48%","lineHeight":"80rpx","fontSize":"28rpx","height":"80rpx"}' @tap="onSubmitTap" class="bg-red">提交</button>
			</view>
		</form>

		<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="clicktimeConfirm" ref="clicktime" themeColor="#333333"></w-picker>
	</view>
</view>
</template>

<script>
	import wPicker from "@/components/w-picker/w-picker.vue";
    import xiaEditor from '@/components/xia-editor/xia-editor';
    import multipleSelect from "@/components/momo-multipleSelect/momo-multipleSelect";
	export default {
		data() {
			return {
				cross:'',
				ruleForm: {
				kechengmingcheng: '',
				fengmian: '',
				jianshenxiangmu: '',
				mubiao: '',
				buwei: '',
				qiangdu: '',
				changdimingcheng: '',
				jiage: '',
				jiaoliangonghao: '',
				jiaolianxingming: '',
				discussnum: '',
				storeupnum: '',
				},
				jianshenxiangmuOptions: [],
				jianshenxiangmuIndex: 0,
				qiangduOptions: [],
				qiangduIndex: 0,
				jiaoliangonghaoOptions: [],
				jiaoliangonghaoIndex: 0,
				// 登录用户信息
				user: {},
                ro:{
                   kechengmingcheng : false,
                   fengmian : false,
                   jianshenxiangmu : false,
                   mubiao : false,
                   buwei : false,
                   qiangdu : false,
                   changdimingcheng : false,
                   jiage : false,
                   jiaoliangonghao : false,
                   jiaolianxingming : false,
                   clicktime : false,
                   clicknum : false,
                   discussnum : false,
                   storeupnum : false,
                },
			}
		},
		components: {
			wPicker,
            xiaEditor,
            multipleSelect,
		},
		computed: {
			baseUrl() {
				return this.$base.url;
			},



		},
		async onLoad(options) {
			let table = uni.getStorageSync("nowTable");
			// 获取用户信息
			let res = await this.$api.session(table);
			this.user = res.data;
			
			// ss读取
			this.ruleForm.jiaoliangonghao = this.user.jiaoliangonghao
			this.ro.jiaoliangonghao = true;
			this.ruleForm.jiaolianxingming = this.user.jiaolianxingming
			this.ro.jiaolianxingming = true;


			// 下拉框
			res = await this.$api.option(`jianshenxiangmu`,`jianshenxiangmu`,{});
			this.jianshenxiangmuOptions = res.data;
            this.jianshenxiangmuOptions.unshift("请选择健身项目");
			// 自定义下拉框值
			this.qiangduOptions = "低级,中级,高级".split(',')
			// 下2
			res = await this.$api.option(`jiaolian`,`jiaoliangonghao`,{});
			this.jiaoliangonghaoOptions = res.data;

			// 如果有登录，获取登录后保存的userid
			this.ruleForm.userid = uni.getStorageSync("appUserid")
			if (options.refid) {
				// 如果上一级页面传递了refid，获取改refid数据信息
				this.ruleForm.refid = options.refid;
				this.ruleForm.nickname = uni.getStorageSync("nickname");
			}
			// 如果是更新操作
			if (options.id) {
				this.ruleForm.id = options.id;
				// 获取信息
				res = await this.$api.info(`jianshenkecheng`, this.ruleForm.id);
				this.ruleForm = res.data;
			}
			// 跨表
			this.cross = options.cross;
			if(options.cross){
				var obj = uni.getStorageSync('crossObj');
				for (var o in obj){
					if(o=='kechengmingcheng'){
					this.ruleForm.kechengmingcheng = obj[o];
					this.ro.kechengmingcheng = true;
					continue;
					}
					if(o=='fengmian'){
					this.ruleForm.fengmian = obj[o].split(",")[0];
					this.ro.fengmian = true;
					continue;
					}
					if(o=='jianshenxiangmu'){
					this.ruleForm.jianshenxiangmu = obj[o];
					this.ro.jianshenxiangmu = true;
					continue;
					}
					if(o=='mubiao'){
					this.ruleForm.mubiao = obj[o];
					this.ro.mubiao = true;
					continue;
					}
					if(o=='buwei'){
					this.ruleForm.buwei = obj[o];
					this.ro.buwei = true;
					continue;
					}
					if(o=='qiangdu'){
					this.ruleForm.qiangdu = obj[o];
					this.ro.qiangdu = true;
					continue;
					}
					if(o=='changdimingcheng'){
					this.ruleForm.changdimingcheng = obj[o];
					this.ro.changdimingcheng = true;
					continue;
					}
					if(o=='jiage'){
					this.ruleForm.jiage = obj[o];
					this.ro.jiage = true;
					continue;
					}
					if(o=='jiaoliangonghao'){
					this.ruleForm.jiaoliangonghao = obj[o];
					this.ro.jiaoliangonghao = true;
					continue;
					}
					if(o=='jiaolianxingming'){
					this.ruleForm.jiaolianxingming = obj[o];
					this.ro.jiaolianxingming = true;
					continue;
					}
					if(o=='clicktime'){
					this.ruleForm.clicktime = obj[o];
					this.ro.clicktime = true;
					continue;
					}
					if(o=='clicknum'){
					this.ruleForm.clicknum = obj[o];
					this.ro.clicknum = true;
					continue;
					}
					if(o=='discussnum'){
					this.ruleForm.discussnum = obj[o];
					this.ro.discussnum = true;
					continue;
					}
					if(o=='storeupnum'){
					this.ruleForm.storeupnum = obj[o];
					this.ro.storeupnum = true;
					continue;
					}
				}
			}
			this.styleChange()
            this.$forceUpdate()
			
			if (uni.getStorageSync('raffleType') && uni.getStorageSync('raffleType') != null) {
				uni.removeStorageSync('raffleType')
				setTimeout(() => {
					this.onSubmitTap()
				}, 300)
			}
		},
		methods: {
			styleChange() {
				this.$nextTick(()=>{
					// document.querySelectorAll('.app-update-pv . .uni-input-input').forEach(el=>{
					//   el.style.backgroundColor = this.addUpdateForm.input.content.backgroundColor
					// })
				})
			},
			// 下二随
			async jiaoliangonghaoChange (e) {
				this.jiaoliangonghaoIndex = e.target.value
				this.ruleForm.jiaoliangonghao = this.jiaoliangonghaoOptions[this.jiaoliangonghaoIndex]
				let res = await this.$api.follow(`jiaolian`, `jiaoliangonghao`,{
					columnValue: this.ruleForm.jiaoliangonghao
				});
				if(res.data.jiaolianxingming){
					this.ruleForm.jiaolianxingming = res.data.jiaolianxingming
				}
			},

			// 多级联动参数


			// 日长控件选择日期时间
			clicktimeConfirm(val) {
				console.log(val)
				this.ruleForm.clicktime = val.result;
				this.$forceUpdate();
			},

			// 下拉变化
			jianshenxiangmuChange(e) {
				this.jianshenxiangmuIndex = e.target.value
				this.ruleForm.jianshenxiangmu = this.jianshenxiangmuOptions[this.jianshenxiangmuIndex]
			},
			// 下拉变化
			qiangduChange(e) {
				this.qiangduIndex = e.target.value
				this.ruleForm.qiangdu = this.qiangduOptions[this.qiangduIndex]
			},

			fengmianTap() {
				let _this = this;
				this.$api.upload(function(res) {
					_this.ruleForm.fengmian = 'upload/' + res.file;
					_this.$forceUpdate();
					_this.$nextTick(()=>{
						_this.styleChange()
					})
				});
			},

			getUUID () {
				return new Date().getTime();
			},
			async onSubmitTap() {
//跨表计算判断
				var obj;
				if((!this.ruleForm.kechengmingcheng)){
					this.$utils.msg(`课程名称不能为空`);
					return
				}
				if((!this.ruleForm.jianshenxiangmu)){
					this.$utils.msg(`健身项目不能为空`);
					return
				}
				if((!this.ruleForm.changdimingcheng)){
					this.$utils.msg(`场地名称不能为空`);
					return
				}
				if(this.ruleForm.jiage&&(!this.$validate.isIntNumer(this.ruleForm.jiage))){
					this.$utils.msg(`每节价格/元应输入整数`);
					return
				}
				if(this.ruleForm.clicknum&&(!this.$validate.isIntNumer(this.ruleForm.clicknum))){
					this.$utils.msg(`点击次数应输入整数`);
					return
				}
				if(this.ruleForm.discussnum&&(!this.$validate.isIntNumer(this.ruleForm.discussnum))){
					this.$utils.msg(`评论数应输入整数`);
					return
				}
				if(this.ruleForm.storeupnum&&(!this.$validate.isIntNumer(this.ruleForm.storeupnum))){
					this.$utils.msg(`收藏数应输入整数`);
					return
				}
				//更新跨表属性
				var crossuserid;
				var crossrefid;
				var crossoptnum;
				if(this.cross){
                    uni.setStorageSync('crossCleanType',true);
					var statusColumnName = uni.getStorageSync('statusColumnName');
					var statusColumnValue = uni.getStorageSync('statusColumnValue');
					if(statusColumnName!='') {
                        if(!obj) {
						    obj = uni.getStorageSync('crossObj');
                        }
						if(!statusColumnName.startsWith("[")) {
							for (var o in obj){
								if(o==statusColumnName){
									obj[o] = statusColumnValue;
								}

							}
							var table = uni.getStorageSync('crossTable');
							await this.$api.update(`${table}`, obj);
						} else {
						       crossuserid=Number(uni.getStorageSync('appUserid'));
						       crossrefid=obj['id'];
						       crossoptnum=uni.getStorageSync('statusColumnName');
						       crossoptnum=crossoptnum.replace(/\[/,"").replace(/\]/,"");
						}
					}
				}
				if(crossrefid && crossuserid) {
					this.ruleForm.crossuserid=crossuserid;
					this.ruleForm.crossrefid=crossrefid;
					let params = {
						page: 1,
						limit:10,
						crossuserid:crossuserid,
						crossrefid:crossrefid,
					}
					let res = await this.$api.list(`jianshenkecheng`, params);
					if (res.data.total >= crossoptnum) {
						this.$utils.msg(uni.getStorageSync('tips'));
                        uni.removeStorageSync('crossCleanType');
						return false;
					} else {
                //跨表计算
						if(this.ruleForm.id){
							await this.$api.update(`jianshenkecheng`, this.ruleForm);
						}else{
							await this.$api.add(`jianshenkecheng`, this.ruleForm);
						}
						this.$utils.msgBack('提交成功');
					}
				} else {
                //跨表计算
					if(this.ruleForm.id){
						await this.$api.update(`jianshenkecheng`, this.ruleForm);
					}else{
						await this.$api.add(`jianshenkecheng`, this.ruleForm);
					}
					this.$utils.msgBack('提交成功');
				}
			},
			optionsChange(e) {
				this.index = e.target.value
			},
			bindDateChange(e) {
				this.date = e.target.value
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
			toggleTab(str) {
				if(this.ro[str]){
					return false
				}
				this.$refs[str].show();
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		min-height: calc(100vh - 44px);
		box-sizing: border-box;
	}
</style>
