<template lang="pug">
.pie
    .pie-chart(:style="{'--percentage' : getStartValuePercent + '%'}")
      .inner
        .pieText
          .pieDescription
            .pieDescription__icon(style="background: #EAC0BB;")
            .pieDescription__text {{getStartValuePercent}}%
          .pieDescription
            .pieDescription__icon(style="background: #A9D3D1;")
            .pieDescription__text {{getPercentValue}}%

</template>

<script>
export default {
  name: 'PieChart',
  props: {
    data: {
      type: Object,
      default: () => {}
    },
    startValue: {
      type: Number,
      default: 15
    },
    maxValue: {
      type: Number,
      default: 86
    },


  },
  computed: {
    getStartValuePercent() {
      return Math.round((this.startValue / this.maxValue) * 100)
    },
    getPercentValue() {
      const percentValue = Math.round(100 - (this.startValue / this.maxValue) * 100)
      return isNaN(percentValue) || !isFinite(percentValue) ? '-' : percentValue
    },
  },

}
</script>

<style lang="scss" scoped>
.pieDescription {
  display: flex;
  align-items: center;
  gap: 5px;
  margin: 2px 0;

  &__icon {
    height: 5px;
    width: 5px;
  }

  &__text {
    color: #9999;
    font-size: 12px;
  }
}

.pieText {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.pie-chart {
  font-size: 14px;
  display: grid;
  place-items: center;
  background: conic-gradient(#EAC0BB 0, #EAC0BB var(--percentage), #A9D3D1 0, #A9D3D1 100%);
  position: relative;
  width: 102px;
  height: 102px;
  margin: 0;
  border-radius: 50%;
}

</style>
