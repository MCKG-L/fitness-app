<template>
<view class="content">
	<view class="box" :style='{"width":"100%","padding":"240rpx 40rpx 0","backgroundSize":"100% 100%","backgroundImage":"url(http://codegen.caihongy.cn/20231206/3555f706e28d4757bbe87fa5f3a2b267.gif)","height":"100%"}'>
		<view :style='{"padding":"30rpx","borderRadius":"40rpx 40rpx 0 0 ","background":"linear-gradient(180deg, rgba(213,224,255,0.5) 0%, rgba(255,255,255,0) 100%)","display":"block","width":"100%","position":"relative","height":"auto"}'>
			<image :style='{"margin":"0 auto 24rpx auto","borderRadius":"8rpx","top":"-180rpx","display":"block","width":"160rpx","position":"absolute","height":"160rpx"}' src="http://codegen.caihongy.cn/20201114/7856ba26477849ea828f481fa2773a95.jpg" mode="aspectFill"></image>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">教练工号：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.jiaoliangonghao"  type="text"  class="uni-input" name="" placeholder="教练工号" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">密码：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.mima" type="password"  class="uni-input" name="" placeholder="密码" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">确认密码：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}' v-model="ruleForm.mima2" type="password" class="uni-input" name="" placeholder="确认密码" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">教练姓名：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.jiaolianxingming"  type="text"  class="uni-input" name="" placeholder="教练姓名" />
			</view>
            <view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">性别：</view>
				<picker :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'"  @change="jiaolianxingbieChange" :value="jiaolianxingbieIndex" :range="jiaolianxingbieOptions">
					<view>
						<view :style='{"padding":"0 30rpx","color":"#1A1A1A","borderRadius":"40rpx","background":"#F8F8F8","flex":"1","display":"inline-block","lineHeight":"88rpx","fontSize":"28rpx","float":"right"}' class="uni-input">{{ruleForm.xingbie?ruleForm.xingbie:"请选择性别"}}</view>
					</view>
				</picker>
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">年龄：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.nianling"  type="text"  class="uni-input" name="" placeholder="年龄" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">身高(cm)：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.shengao"  type="text"  class="uni-input" name="" placeholder="身高(cm)" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">体重(kg)：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.tizhong"  type="text"  class="uni-input" name="" placeholder="体重(kg)" />
			</view>
            <view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" @tap="jiaolianzhaopianTap" class="">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">照片：</view>
				<image :style='{"width":"80rpx","borderRadius":"40rpx","background":"#0060C8","display":"block","height":"80rpx"}' v-if="ruleForm.zhaopian" class="avator" :src="baseUrl+ruleForm.zhaopian" mode=""></image>
                <image :style='{"width":"80rpx","borderRadius":"40rpx","background":"#0060C8","display":"block","height":"80rpx"}' v-else class="avator" src="../../static/gen/upload.png" mode=""></image>
            </view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='jiaolian'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">教龄：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.jiaoling"  type="text"  class="uni-input" name="" placeholder="教龄" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">用户账号：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.yonghuzhanghao"  type="text"  class="uni-input" name="" placeholder="用户账号" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">密码：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.mima" type="password"  class="uni-input" name="" placeholder="密码" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">确认密码：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}' v-model="ruleForm.mima2" type="password" class="uni-input" name="" placeholder="确认密码" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">用户姓名：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.yonghuxingming"  type="text"  class="uni-input" name="" placeholder="用户姓名" />
			</view>
            <view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" @tap="huiyuantouxiangTap" class="">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">头像：</view>
				<image :style='{"width":"80rpx","borderRadius":"40rpx","background":"#0060C8","display":"block","height":"80rpx"}' v-if="ruleForm.touxiang" class="avator" :src="baseUrl+ruleForm.touxiang" mode=""></image>
                <image :style='{"width":"80rpx","borderRadius":"40rpx","background":"#0060C8","display":"block","height":"80rpx"}' v-else class="avator" src="../../static/gen/upload.png" mode=""></image>
            </view>
            <view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">性别：</view>
				<picker :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'"  @change="huiyuanxingbieChange" :value="huiyuanxingbieIndex" :range="huiyuanxingbieOptions">
					<view>
						<view :style='{"padding":"0 30rpx","color":"#1A1A1A","borderRadius":"40rpx","background":"#F8F8F8","flex":"1","display":"inline-block","lineHeight":"88rpx","fontSize":"28rpx","float":"right"}' class="uni-input">{{ruleForm.xingbie?ruleForm.xingbie:"请选择性别"}}</view>
					</view>
				</picker>
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">年龄：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.nianling"  type="text"  class="uni-input" name="" placeholder="年龄" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">身高(cm)：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.shengao"  type="text"  class="uni-input" name="" placeholder="身高(cm)" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">体重(kg)：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.tizhong"  type="text"  class="uni-input" name="" placeholder="体重(kg)" />
			</view>
			<view :style='{"width":"100%","margin":"0 0 24rpx 0","display":"flex","height":"auto"}' v-if="tableName=='huiyuan'" class="uni-form-item uni-column">
				<view :style='{"width":"188rpx","lineHeight":"88rpx","fontSize":"28rpx","color":"#A1A1A1"}' class="label">手机号码：</view>
				<input :style='{"border":"0px solid rgb(255, 170, 51)","padding":"0px 24rpx","margin":"0px","color":"rgb(0, 0, 0)","borderRadius":"40rpx","flex":"1","background":"#F8F8F8","fontSize":"28rpx","height":"88rpx"}'  v-model="ruleForm.shoujihaoma"  type="text"  class="uni-input" name="" placeholder="手机号码" />
			</view>
			<button :style='{"border":"0","padding":"0px","margin":"0 0 24rpx 0","color":"rgb(255, 255, 255)","borderRadius":"40rpx","background":"#0060c8","width":"100%","lineHeight":"88rpx","fontSize":"32rpx","height":"88rpx"}' class="btn-submit" @tap="register" type="primary">注册</button>
			
			<view class="idea1" :style='{"width":"100%","background":"red","display":"none","height":"80rpx"}'>idea1</view>
			<view class="idea2" :style='{"width":"100%","background":"red","display":"none","height":"80rpx"}'>idea2</view>
			<view class="idea3" :style='{"width":"100%","background":"red","display":"none","height":"80rpx"}'>idea3</view>
		</view>
	</view>
</view>
</template>

<script>
    import multipleSelect from "@/components/momo-multipleSelect/momo-multipleSelect";
	export default {
		data() {
			return {
                jiaolianxingbieOptions: [],
                jiaolianxingbieIndex: 0,
                huiyuanxingbieOptions: [],
                huiyuanxingbieIndex: 0,
				ruleForm: {
                jiaoliangonghao: '',
                mima: '',
                jiaolianxingming: '',
                xingbie: '',
                nianling: '',
                shengao: '',
                tizhong: '',
                zhaopian: '',
                jiaoling: '',
                jiaolianjieshao: '',
                status: '',
                yonghuzhanghao: '',
                mima: '',
                yonghuxingming: '',
                touxiang: '',
                xingbie: '',
                nianling: '',
                shengao: '',
                tizhong: '',
                shoujihaoma: '',
				},
				tableName:""
			}
		},
        components: {
            multipleSelect
        },
        computed: {
            baseUrl() {
                return this.$base.url;
            },
        },
		async onLoad() {
			let res = [];
			let table = uni.getStorageSync("loginTable");
            this.tableName = table;

                        // 自定义下拉框值
			if(this.tableName=='jiaolian'){
                this.jiaolianxingbieOptions = "男,女".split(',');
				this.ruleForm.xingbie=this.jiaolianxingbieOptions[0]
			}
                        // 自定义下拉框值
			if(this.tableName=='huiyuan'){
                this.huiyuanxingbieOptions = "男,女".split(',');
				this.ruleForm.xingbie=this.huiyuanxingbieOptions[0]
			}
			
			this.styleChange()
		},
		methods: {

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
					// document.querySelectorAll('.uni-input .uni-input-input').forEach(el=>{
					//   el.style.backgroundColor = this.registerFrom.content.input.backgroundColor
					// })
				})
			},
			// 获取uuid
			getUUID () {
				return new Date().getTime();
			},
			// 注册
			async register() {
				if(`jiaolian` == this.tableName && (this.ruleForm.jiaoliangonghao.length<6)){
					this.$utils.msg(`教练工号长度不能小于6`);
					return
				}
				if(`jiaolian` == this.tableName && (this.ruleForm.jiaoliangonghao.length>8)){
					this.$utils.msg(`教练工号长度不能大于8`);
					return
				}
                if(`jiaolian` == this.tableName && (this.ruleForm.mima!=this.ruleForm.mima2)){
                    this.$utils.msg(`两次密码输入不一致`);
                    return
                }
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
                if(`huiyuan` == this.tableName && (this.ruleForm.mima!=this.ruleForm.mima2)){
                    this.$utils.msg(`两次密码输入不一致`);
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
				await this.$api.register(`${this.tableName}`, this.ruleForm);
				this.$utils.msgBack('注册成功');;
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
