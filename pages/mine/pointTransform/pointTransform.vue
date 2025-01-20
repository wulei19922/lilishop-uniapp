<template>
  <view class="container">
    <view class="header">
      <view class="balance">
        <text class="label">A积分:</text>
        <text class="value">{{ aBalance }}</text>
      </view>
      <view class="balance">
        <text class="label">B积分:</text>
        <text class="value">{{ bBalance }}</text>
      </view>
      <view class="balance">
        <text class="label">C积分:</text>
        <text class="value">{{ cBalance }}</text>
      </view>
    </view>
    <view class="input-container">
      <input v-model="exchangeAmount" type="number" placeholder="输入兑换数字" />
      <button @click="exchange">兑换</button>
    </view>
    <view class="message" v-if="message">{{ message }}</view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      aBalance: 100, // A积分余额
      bBalance: 50, // B积分余额
      cBalance: 30, // C积分余额
      exchangeAmount: 0, // 兑换数量
      message: '' // 提示信息
    }
  },
  methods: {
    exchange() {
      if (this.exchangeAmount > this.aBalance) {
        this.message = 'A积分不足'
      } else if (this.exchangeAmount > this.cBalance) {
        this.message = 'C积分不足'
      } else {
        this.aBalance -= this.exchangeAmount
        this.bBalance += this.exchangeAmount
        this.cBalance -= this.exchangeAmount
        this.message = '兑换成功'
      }
    }
  }
}
</script>

<style scoped>
.container {
  padding: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.balance {
  display: flex;
  align-items: center;
}

.label {
  margin-right: 10px;
}

.input-container {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

input {
  flex: 1;
  margin-right: 10px;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  padding: 5px 10px;
  background-color: #007aff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.message {
  text-align: center;
  color: red;
}
</style>