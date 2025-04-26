<template>
<view class="content">
	<view :style='{"minHeight":"100vh","width":"100%","padding":"20rpx 40rpx","position":"relative","background":"#edeff3","height":"auto"}'>
		<form :style='{"width":"100%","padding":"24rpx","background":"#edeff3","display":"block","height":"auto"}' class="app-update-pv">
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">课程名称</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.kechengmingcheng" v-model="ruleForm.kechengmingcheng" placeholder="课程名称"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">健身项目</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.jianshenxiangmu" v-model="ruleForm.jianshenxiangmu" placeholder="健身项目"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">强度</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.qiangdu" v-model="ruleForm.qiangdu" placeholder="强度"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">场地名称</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.changdimingcheng" v-model="ruleForm.changdimingcheng" placeholder="场地名称"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">每节价格/元</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.jiage" v-model="ruleForm.jiage" placeholder="每节价格/元" type="number"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">节数</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.jieshu" v-model="ruleForm.jieshu" placeholder="节数" type="number"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">应付金额</view>
				<view :style='{"padding":"0px 24rpx","margin":"0px","lineHeight":"80rpx","fontSize":"28rpx","color":"rgb(0, 0, 0)","flex":"1"}' class="right-input">
					{{yingfujine}}
				</view>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">用户账号</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.yonghuzhanghao" v-model="ruleForm.yonghuzhanghao" placeholder="用户账号"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">用户姓名</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.yonghuxingming" v-model="ruleForm.yonghuxingming" placeholder="用户姓名"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">教练工号</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.jiaoliangonghao" v-model="ruleForm.jiaoliangonghao" placeholder="教练工号"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">教练姓名</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0px","color":"#000000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' :disabled="ro.jiaolianxingming" v-model="ruleForm.jiaolianxingming" placeholder="教练姓名"  type="text"></input>
			</view>
			<view :style='{"padding":"12rpx 0","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0 0 2rpx 0","background":"#fff","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class="" @tap="fengmianTap">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E","textAlign":"right"}' class="title">封面</view>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' class="avator" v-if="ruleForm.fengmian" :src="baseUrl+ruleForm.fengmian.split(',')[0]" mode="aspectFill"></image>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' class="avator" v-else src="../../static/gen/upload.png" mode="aspectFill"></image>
			</view>
 

			
			<view :style='{"width":"100%","justifyContent":"space-between","display":"flex","height":"auto"}' class="btn" >
				<button :style='{"border":"0","padding":"0px","margin":"0","color":"rgb(255, 255, 255)","borderRadius":"60rpx","background":"#0060c8","width":"48%","lineHeight":"80rpx","fontSize":"28rpx","height":"80rpx"}' @tap="onSubmitTap" class="bg-red">提交</button>
			</view>
		</form>

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
				jianshenxiangmu: '',
				qiangdu: '',
				changdimingcheng: '',
				jiage: '',
				jieshu: '',
				yingfujine: '',
				yonghuzhanghao: '',
				yonghuxingming: '',
				jiaoliangonghao: '',
				jiaolianxingming: '',
				fengmian: '',
				ispay: '',
				},
				// 登录用户信息
				user: {},
                ro:{
                   kechengmingcheng : false,
                   jianshenxiangmu : false,
                   qiangdu : false,
                   changdimingcheng : false,
                   jiage : false,
                   jieshu : false,
                   yingfujine : false,
                   yonghuzhanghao : false,
                   yonghuxingming : false,
                   jiaoliangonghao : false,
                   jiaolianxingming : false,
                   fengmian : false,
                   ispay : false,
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


			yingfujine:{
			get: function () {
				return 1*this.ruleForm.jiage*this.ruleForm.jieshu
			}
			},

		},
		async onLoad(options) {
			let table = uni.getStorageSync("nowTable");
			// 获取用户信息
			let res = await this.$api.session(table);
			this.user = res.data;
			
			// ss读取
			this.ruleForm.yonghuzhanghao = this.user.yonghuzhanghao
			this.ro.yonghuzhanghao = true;
			this.ruleForm.yonghuxingming = this.user.yonghuxingming
			this.ro.yonghuxingming = true;



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
				res = await this.$api.info(`kechengdingdan`, this.ruleForm.id);
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
					if(o=='jianshenxiangmu'){
					this.ruleForm.jianshenxiangmu = obj[o];
					this.ro.jianshenxiangmu = true;
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
					if(o=='jieshu'){
					this.ruleForm.jieshu = obj[o];
					this.ro.jieshu = true;
					continue;
					}
					if(o=='yingfujine'){
					this.ruleForm.yingfujine = obj[o];
					this.ro.yingfujine = true;
					continue;
					}
					if(o=='yonghuzhanghao'){
					this.ruleForm.yonghuzhanghao = obj[o];
					this.ro.yonghuzhanghao = true;
					continue;
					}
					if(o=='yonghuxingming'){
					this.ruleForm.yonghuxingming = obj[o];
					this.ro.yonghuxingming = true;
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
					if(o=='fengmian'){
					this.ruleForm.fengmian = obj[o].split(",")[0];
					this.ro.fengmian = true;
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

			// 多级联动参数




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
				this.ruleForm.yingfujine = this.yingfujine
//跨表计算判断
				var obj;
				if(this.ruleForm.jiage&&(!this.$validate.isIntNumer(this.ruleForm.jiage))){
					this.$utils.msg(`每节价格/元应输入整数`);
					return
				}
				if((!this.ruleForm.jieshu)){
					this.$utils.msg(`节数不能为空`);
					return
				}
				if(this.ruleForm.jieshu&&(!this.$validate.isIntNumer(this.ruleForm.jieshu))){
					this.$utils.msg(`节数应输入整数`);
					return
				}
				if(this.ruleForm.yingfujine&&(!this.$validate.isIntNumer(this.ruleForm.yingfujine))){
					this.$utils.msg(`应付金额应输入整数`);
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
					let res = await this.$api.list(`kechengdingdan`, params);
					if (res.data.total >= crossoptnum) {
						this.$utils.msg(uni.getStorageSync('tips'));
                        uni.removeStorageSync('crossCleanType');
						return false;
					} else {
                //跨表计算
						if(this.ruleForm.id){
							await this.$api.update(`kechengdingdan`, this.ruleForm);
						}else{
							await this.$api.add(`kechengdingdan`, this.ruleForm);
						}
						this.$utils.msgBack('提交成功');
					}
				} else {
                //跨表计算
					if(this.ruleForm.id){
						await this.$api.update(`kechengdingdan`, this.ruleForm);
					}else{
						await this.$api.add(`kechengdingdan`, this.ruleForm);
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
