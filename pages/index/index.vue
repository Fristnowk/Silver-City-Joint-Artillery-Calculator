<template>
  <view class="container">
    <view class="card">
      <p style="margin-top: 10px">双方手牌及场上牌总合</p>
      <input
        v-model.number="totalCards"
        placeholder="双方手牌及场上牌总合"
        type="number"
        class="input-field"
      />
      <p>对方怪兽阶级（用空格分隔）</p>
      <input
        v-model="monsterRanks"
        placeholder="对方怪兽阶级（用空格分隔）"
        class="input-field"
      />

      <!-- 显示每个怪兽阶级的详细信息 -->
      <view class="result-section" v-if="monsterRankDetails.length > 0">
        <view
          class="result-card"
          v-for="(rank, index) in monsterRankDetails"
          :key="index"
        >
          <p>
            怪兽阶级: <strong>{{ rank.rank }}</strong>
          </p>
          <p>
            需要除外的超量怪兽阶级: <strong>{{ rank.excludedXyz }}*2只</strong>
          </p>
          <p>
            需要除外的融合怪兽阶级: <strong>{{ rank.excludedFusion }}</strong>
          </p>
        </view>
      </view>
    </view>
  </view>
</template>

<script setup>
import { ref, reactive, watch } from 'vue';

const totalCards = ref(0);
const monsterRanks = ref('');
const monsterRankDetails = reactive([]);

// 自动计算函数
const autoCalculate = () => {
  const ranks = monsterRanks.value
    .trim()
    .split(/\s+/)
    .filter(Boolean)
    .map(Number);
  monsterRankDetails.splice(0); // 清空旧数据

  ranks.forEach((rank) => {
    const excludedXyz = totalCards.value - rank;
    const excludedFusion = rank - excludedXyz;
    monsterRankDetails.push({
      rank,
      excludedXyz,
      excludedFusion,
    });
  });
};

// 监听输入变化，自动计算
watch([totalCards, monsterRanks], autoCalculate, { deep: true });

// 初始化时也执行一次
autoCalculate();
</script>

<style>
.container {
  padding: 20rpx;
  background-color: #f5f5f5;
  min-height: 100vh;
}

.card {
  background-color: white;
  border-radius: 16rpx;
  box-shadow: 0 4rpx 20rpx rgba(0, 0, 0, 0.1);
  padding: 40rpx;
  margin: 0 auto;
  max-width: 800rpx;
}

.input-field {
  height: 80rpx;
  border: 1px solid #ccc;
  border-radius: 8rpx;
  padding: 0 20rpx;
  margin-bottom: 30rpx;
  font-size: 28rpx;
}

.result-section {
  margin-top: 40rpx;
}

.result-card {
  background-color: #f9f9f9;
  border: 1px solid #eee;
  border-radius: 12rpx;
  padding: 30rpx;
  margin-bottom: 20rpx;
}
</style>
