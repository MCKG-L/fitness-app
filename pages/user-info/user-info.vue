<template>
<view class="content">
	<view class="box" :style='{"width":"100%","padding":"20rpx 40rpx","position":"relative","background":"#EDEFF3","height":"100vh"}'>
		<view :style='{"width":"100%","padding":"24rpx","background":"#EDEFF3","display":"block","height":"auto"}'>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>教练工号</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' disabled="true"  v-model="ruleForm.jiaoliangonghao" placeholder="教练工号"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>教练姓名</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.jiaolianxingming" placeholder="教练姓名"></input>
			</view>
			<view v-if="tableName=='jiaolian'" :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class=" select">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}' class="title">性别</view>
				<picker :style='{"width":"100%","flex":"1","height":"auto"}'  @change="jiaolianxingbieChange" :value="jiaolianxingbieIndex" :range="jiaolianxingbieOptions">
					<view :style='{"width":"100%","lineHeight":"80rpx","fontSize":"28rpx","color":"#040000"}' class="uni-input picker-select-input">{{ruleForm.xingbie?ruleForm.xingbie:"请选择性别"}}</view>
				</picker>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>年龄</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.nianling" placeholder="年龄"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>身高(cm)</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.shengao" placeholder="身高(cm)"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>体重(kg)</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.tizhong" placeholder="体重(kg)"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" @tap="jiaolianzhaopianTap" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>照片</view>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' v-if="ruleForm.zhaopian" style="margin: 0;" class="avator" :src="baseUrl+ruleForm.zhaopian" mode=""></image>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' v-else class="avator" style="margin: 0;" src="../../static/gen/upload.png" mode=""></image>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>教龄</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.jiaoling" placeholder="教龄"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}' class="title">教练介绍</view>
                <xia-editor ref="editor" :style='{"minHeight":"300rpx","border":"0px solid #efefef","padding":"10rpx","flex":"1","background":"#EDEFF3","height":"auto"}' v-model="ruleForm.jiaolianjieshao" placeholder="教练介绍" @editorChange="jiaolianjieshaoChange"></xia-editor>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='huiyuan'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>用户账号</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}' disabled="true"  v-model="ruleForm.yonghuzhanghao" placeholder="用户账号"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='huiyuan'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>用户姓名</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.yonghuxingming" placeholder="用户姓名"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='huiyuan'" @tap="huiyuantouxiangTap" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>头像</view>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' v-if="ruleForm.touxiang" style="margin: 0;" class="avator" :src="baseUrl+ruleForm.touxiang" mode=""></image>
				<image :style='{"width":"80rpx","borderRadius":"100%","objectFit":"cover","display":"block","height":"80rpx"}' v-else class="avator" style="margin: 0;" src="../../static/gen/upload.png" mode=""></image>
			</view>
			<view v-if="tableName=='huiyuan'" :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' class=" select">
				<view :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}' class="title">性别</view>
				<picker :style='{"width":"100%","flex":"1","height":"auto"}'  @change="huiyuanxingbieChange" :value="huiyuanxingbieIndex" :range="huiyuanxingbieOptions">
					<view :style='{"width":"100%","lineHeight":"80rpx","fontSize":"28rpx","color":"#040000"}' class="uni-input picker-select-input">{{ruleForm.xingbie?ruleForm.xingbie:"请选择性别"}}</view>
				</picker>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='huiyuan'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>年龄</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.nianling" placeholder="年龄"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='huiyuan'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>身高(cm)</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.shengao" placeholder="身高(cm)"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='huiyuan'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>体重(kg)</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.tizhong" placeholder="体重(kg)"></input>
			</view>
			<view :style='{"padding":"12rpx 20rpx","margin":"0 0 24rpx 0","borderColor":"#ccc","alignItems":"center","borderRadius":"80rpx","borderWidth":"0","background":"#FFFFFF","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}' v-if="tableName=='huiyuan'" class="">
				<view class="title" :style='{"width":"180rpx","padding":"0 20rpx 0 0","lineHeight":"80rpx","fontSize":"28rpx","color":"#9E9E9E"}'>手机号码</view>
				<input :style='{"border":"0","padding":"0px 24rpx","margin":"0","color":"#040000","borderRadius":"8rpx","flex":"1","background":"rgba(255, 255, 255, 0)","fontSize":"28rpx","height":"80rpx"}'   v-model="ruleForm.shoujihaoma" placeholder="手机号码"></input>
			</view>
			<view :style='{"width":"100%","justifyContent":"center","display":"flex","height":"auto"}' class="btn">
				<button @tap="update()" class="cu-btn lg" :style='{"border":"0","padding":"0px","margin":"0 20rpx","color":"rgb(255, 255, 255)","borderRadius":"60rpx","background":"#0060C8","width":"248rpx","lineHeight":"80rpx","fontSize":"28rpx","height":"80rpx"}'>保存</button>
				<button @tap="logout()" class="cu-btn lg" :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px","margin":"0 20rpx","color":"#848484","borderRadius":"80rpx","background":"#d4d4d4","width":"248rpx","lineHeight":"80rpx","fontSize":"28rpx","height":"80rpx"}'>退出登录</button>
			</view>
		</view>
	</view>
</view>
</template>

<script>

    import xiaEditor from '@/components/xia-editor/xia-editor';
    import multipleSelect from "@/components/momo-multipleSelect/momo-multipleSelect";
	export default {
		data() {
			return {
				ruleForm: {
				},
				tableName:"",
				jiaolianxingbieOptions: [],
				jiaolianxingbieIndex: 0,
				huiyuanxingbieOptions: [],
				huiyuanxingbieIndex: 0,
			}
		},
        components: {
            multipleSelect,
			xiaEditor
        },
		computed: {
			baseUrl() {
				return this.$base.url;
			}
		},
		async onLoad() {
			let table = uni.getStorageSync("nowTable");
			let that = this
			let res = {}
			this.tableName = table;
			this.getSession()
			// 自定义下拉框值
			if(this.tableName=='jiaolian'){
				this.jiaolianxingbieOptions = "男,女".split(',');
				this.jiaolianxingbieOptions.forEach((item, index) => {
					if(item==this.ruleForm.xingbie) {
						this.jiaolianxingbieIndex = index;
					}
				});
			}
			// 自定义下拉框值
			if(this.tableName=='huiyuan'){
				this.huiyuanxingbieOptions = "男,女".split(',');
				this.huiyuanxingbieOptions.forEach((item, index) => {
					if(item==this.ruleForm.xingbie) {
						this.huiyuanxingbieIndex = index;
					}
				});
			}
			this.styleChange()
            this.$forceUpdate()
		},
		methods: {
			async getSession(){
				let res = await this.$api.session(this.tableName)
				this.ruleForm = res.data;
			},
            // 下拉变化
            jiaolianxingbieChange(e) {
                    this.jiaolianxingbieIndex = e.target.value
                    this.ruleForm.xingbie = this.jiaolianxingbieOptions[this.jiaolianxingbieIndex]
            },
			jiaolianzhaopianTap() {
				let _this = this;
				this.$api.upload(function(res) {
					_this.ruleForm.zhaopian = 'upload/' + res.file;
					_this.$forceUpdate();
				});
			},
            jiaolianjieshaoChange(e) {
                this.ruleForm.jiaolianjieshao = e
            },
			huiyuantouxiangTap() {
				let _this = this;
				this.$api.upload(function(res) {
					_this.ruleForm.touxiang = 'upload/' + res.file;
					_this.$forceUpdate();
				});
			},
            // 下拉变化
            huiyuanxingbieChange(e) {
                    this.huiyuanxingbieIndex = e.target.value
                    this.ruleForm.xingbie = this.huiyuanxingbieOptions[this.huiyuanxingbieIndex]
            },

            toggleTab(str) {
                this.$refs[str].show();
            },

			styleChange() {
				this.$nextTick(()=>{
					// document.querySelectorAll('. .uni-input-input').forEach(el=>{
					//   el.style.backgroundColor = this.userInfoForm.list.input.backgroundColor
					// })
				})
			},
			// 获取uuid
			getUUID () {
				return new Date().getTime();
			},
			logout() {
				uni.clearStorageSync()
				this.$utils.jump('../login/login');
			},
			// 注册
			async update() {






				if(`jiaolian` == this.tableName && this.ruleForm.shengao&&(!this.$validate.isNumber(this.ruleForm.shengao))){
					this.$utils.msg(`身高(cm)应输入数字`);
					return
				}

				if(`jiaolian` == this.tableName && this.ruleForm.tizhong&&(!this.$validate.isNumber(this.ruleForm.tizhong))){
					this.$utils.msg(`体重(kg)应输入数字`);
					return
				}


				if(`jiaolian` == this.tableName && this.ruleForm.jiaoling&&(!this.$validate.isNumber(this.ruleForm.jiaoling))){
					this.$utils.msg(`教龄应输入数字`);
					return
				}


				if(`jiaolian` == this.tableName && this.ruleForm.status&&(!this.$validate.isIntNumer(this.ruleForm.status))){
					this.$utils.msg(`状态应输入整数`);
					return
				}


				if((!this.ruleForm.mima) && `huiyuan` == this.tableName){
					this.$utils.msg(`密码不能为空`);
					return
				}

				if((!this.ruleForm.yonghuxingming) && `huiyuan` == this.tableName){
					this.$utils.msg(`用户姓名不能为空`);
					return
				}



				if(`huiyuan` == this.tableName && this.ruleForm.nianling&&(!this.$validate.isIntNumer(this.ruleForm.nianling))){
					this.$utils.msg(`年龄应输入整数`);
					return
				}

				if(`huiyuan` == this.tableName && this.ruleForm.shengao&&(!this.$validate.isNumber(this.ruleForm.shengao))){
					this.$utils.msg(`身高(cm)应输入数字`);
					return
				}

				if(`huiyuan` == this.tableName && this.ruleForm.tizhong&&(!this.$validate.isNumber(this.ruleForm.tizhong))){
					this.$utils.msg(`体重(kg)应输入数字`);
					return
				}

				if(`huiyuan` == this.tableName && this.ruleForm.shoujihaoma&&(!this.$validate.isMobile(this.ruleForm.shoujihaoma))){
					this.$utils.msg(`手机号码应输入手机格式`);
					return
				}
				let table = uni.getStorageSync("nowTable");
				await this.$api.update(table, this.ruleForm);
				this.$utils.msgBack('修改成功');;
				this.getSession()
			},

		}
	}
</script>

<style lang="scss" scoped>
	.content {
		min-height: calc(100vh - 44px);
		box-sizing: border-box;
	}
</style>
