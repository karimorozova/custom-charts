<template lang="pug">
.lineBarChart
    .label(v-if="isLabels")
      .label__text {{ series[0] }}{{ symbol }}
      .label__text(style="opacity: .8") /
      .label__text {{ series[1] }}{{ symbol }}

    .lineBar(
      :style="{'height': height + 'px', 'width': width  + 'px'}"
    )
      .lineBar__range( :style="{'background': colors[0], 'width': series[0] + '%' }" )
      .lineBar__splitter(v-if="isSplitter")
      .lineBar__range( :style="{'background': colors[1], 'width': series[1] + '%' }" )

</template>

<script>

export default {
  name: "LineBarChart",

  props: {
    height: {
      type: Number,
      default: 7
    },
    width: {
      type: Number,
      default: 140
    },
    series: {
      type: Array,
      default: () => [ 50, 50 ]
    },
    colors: {
      type: Array,
      default: () => [ '#d66f58', '#4ba5a5'] 
    },
    symbol: {
      type: String,
      default: "%"
    },
    isLabels: {
      type: Boolean,
      default: true
    },
    isSplitter: {
      type: Boolean,
      default: true
    }
  }
}
</script>

<style lang="scss" scoped>

.lineBar {
  display: flex;

  &__splitter {
    width: 2px;
    background: transparent;
  }
}

.label {
  display: flex;
  justify-content: center;
  gap: 4px;
  font-size: 12px;
  color: gray;
  margin-bottom: 4px;
}
</style>
