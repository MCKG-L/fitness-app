<template>
  <view class="exercise-selection-container" v-if="!selectedExercise">
    <view class="exercise-title">选择你的动作</view>
    <view class="exercise-grid">
      <view
        class="exercise-card"
        v-for="exercise in exercises"
        :key="exercise.id"
        @tap="selectExercise(exercise)"
      >
        <view class="exercise-name">{{ exercise.name }}</view>
      </view>
    </view>
  </view>

  <view class="exercise-display-container" v-else>
    <view class="selected-exercise-name">{{ selectedExercise.name }}</view>
    <camera id="camera" device-position="front" flash="off" style="width: 100%; height: 500rpx;" />

    <!-- 显示返回的图片 -->
    <view v-if="imageBase64" class="result-image-container">
      <image :src="'data:image/jpeg;base64,' + imageBase64" style="width: 100%; height: 500rpx;" />
    </view>

    <view v-if="exerciseFeedback" class="exercise-result">
      <view>分析结果：</view>
      <template v-if="exerciseFeedback.elbow_angle !== undefined">
        <view>肘部角度: {{ exerciseFeedback.elbow_angle.toFixed(2) }}°</view>
      </template>
    </view>

    <button @tap="stopExercise" class="stop-button">结束动作</button>
  </view>
</template>

<script>
export default {
  data() {
    return {
      exercises: [
        { id: 'curl', name: '弯曲检测' },
        { id: 'high-knee', name: '高抬腿检测' },
        { id: 'jump', name: '跳跃检测' },
        { id: 'jumping-jack', name: '开合跳检测' },
        { id: 'lunge', name: '弓步检测' },
        { id: 'plank', name: '平板支撑检测' },
        { id: 'push-up', name: '俯卧撑检测' },
        { id: 'sit-up', name: '仰卧起坐检测' }
      ],
      selectedExercise: null,
      exerciseFeedback: null,
      imageBase64: null,  // 用于存储返回的Base64图像数据
      intervalId: null,
      baseUrl: 'http://192.168.137.76:5000'
    };
  },

  methods: {
    async selectExercise(exercise) {
      this.selectedExercise = exercise;
      try {
        this.startExerciseAnalysis();
      } catch (e) {
        console.error('摄像头初始化失败', e);
        uni.showToast({ title: '摄像头启动失败', icon: 'none' });
      }
    },

    startExerciseAnalysis() {
      const cameraContext = uni.createCameraContext();
      this.intervalId = setInterval(() => {
        cameraContext.takePhoto({
          quality: 'low',
          success: res => {
            uni.getFileSystemManager().readFile({
              filePath: res.tempImagePath,
              encoding: 'base64',
              success: fileRes => {
                const frameDataUrl = fileRes.data;
                this.sendFrameToBackend(frameDataUrl);
              },
              fail: err => {
                console.error('读取图片失败', err);
              }
            });
          },
          fail: err => {
            console.error('拍照失败', err);
          }
        });
      }, 100); // 每秒拍一帧
    },

    sendFrameToBackend(base64Image) {
      const url = `${this.baseUrl}/pose_estimation/${this.selectedExercise.id}`;
      const token = { Token: uni.getStorageSync("appToken") };
      const header = Object.assign({ 'Content-Type': 'application/json' }, token);

      new Promise((resolve, reject) => {
        uni.request({
          url,
          method: 'POST',
          data: { image: base64Image },
          header: header,
          dataType: 'json',
          complete: (response) => {
            const statusCode = response.statusCode;
            if (statusCode === 200) {
              const rs = response.data;
              if (rs.code === 0) {
                resolve(rs);
              } else {
                uni.showToast({ title: rs.msg, icon: 'none', duration: 2000 });
                reject(rs);
              }
            } else {
              uni.showToast({ title: '接口执行异常', icon: 'none', duration: 2000 });
              reject(response);
            }
          }
        });
      })
      .then(res => {

        // 处理返回的图片Base64数据
        this.imageBase64 = res.data.image;  // 假设接口返回字段为 image_base64
        // console.log("返回的base64：", this.imageBase64);
        // 设置反馈信息
        this.exerciseFeedback = {
          elbow_angle: res.data.exercise_results.elbow_angle,
          feedback: res.data.exercise_results.feedback || ["无反馈信息"]
        };
      })
      .catch(err => {
        console.error('分析失败:', err);
        uni.showToast({ title: '分析失败', icon: 'none' });
      });
    },

    stopExercise() {
      clearInterval(this.intervalId);
      this.intervalId = null;
      this.selectedExercise = null;
      this.exerciseFeedback = null;
      this.imageBase64 = null;  // 清空图像
    }
  }
};
</script>

<style scoped>
.exercise-selection-container {
  text-align: center;
  padding: 20px;
}
.exercise-title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
}
.exercise-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 16px;
}
.exercise-card {
  background-color: #fff;
  border: 1px solid #ccc;
  padding: 12px;
  border-radius: 8px;
}
.exercise-name {
  font-size: 18px;
}
.exercise-display-container {
  padding: 20px;
}
.result-image-container {
  margin-top: 20px;
}
.exercise-result {
  background-color: #f6f6f6;
  margin-top: 12px;
  padding: 10px;
  border-radius: 6px;
  word-break: break-all;
}
.stop-button {
  margin-top: 20px;
  background-color: #f44336;
  color: white;
  padding: 10px;
  border-radius: 6px;
  border: none;
}
</style>
