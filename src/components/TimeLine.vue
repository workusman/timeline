<template>
  <div class="block">
    <h3 class="order">Order</h3>
    <div class="radio">
      <el-radio-group v-model="reverse">
        <el-radio :label="true" border size="medium">descending</el-radio>
        <el-radio :label="false" border size="medium">ascending</el-radio>
      </el-radio-group>
    </div>
    <ul :reverse="reverse" class="timeline">
      <el-tooltip
        :content="activity.content"
        v-for="(activity, index) in activities"
        :key="index"
        :timestamp="activity.timestamp"
      >
        <li class="timeline-item" :class="activity.icon" />
      </el-tooltip>
    </ul>
  </div>
</template>

<script>
import activities from "../data/activities";

export default {
  name: "TimeLine",
  data() {
    return {
      reverse: false,
      activities: activities,
    };
  },
  watch: {
    reverse() {
      this.activities = this.activities.slice().reverse();
    },
  },
};
</script>

<style lang="scss" scoped>
.radio {
  text-align: center;
}
.order {
  text-align: center;
}
.timeline {
  align-content: center;
  align-items: center;
  display: flex;
  /* justify-content: space-around; */
  font-size: 14px;
  margin-top: 30px;
  .timeline-item {
    background: #98b9fb;
    color: white;
    content: " ";
    display: flex;
    flex-grow: 1;
    height: 2px;
    line-height: 1em;
    margin: 0;
    position: relative;
    text-align: right;
    z-index: 1;
    &::before {
      color: white;
      background: #98b9fb;
      border-radius: 50%;
      height: 2em;
      left: -2em;
      line-height: 2em;
      position: absolute;
      text-align: center;
      top: -0.85em;
      width: 2em;
    }
    &:last-child {
      flex-basis: 0;
      flex-grow: 0;
      flex-shrink: 1;
    }
  }
}
</style>
