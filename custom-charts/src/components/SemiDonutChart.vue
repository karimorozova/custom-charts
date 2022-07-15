<template lang="pug">
.semiDonutChart(:style="{'height': height + 'px', 'width': width  + 'px'}")
    .graph__text(v-if="isLabels")
      .graph__description
        .graph__description-icon(:style="{background: colors[1]}")
        .graph__description-text {{series[1]}}%
      .graph__description
        .graph__description-icon(:style="{background: colors[0]}")
        .graph__description-text {{series[0]}}%

    .multi-graph
      .graph( :style="{'--percentage' : 100, '--fill': colors[0]}")
      .graph( :style="{'--percentage' : series[1], '--fill': colors[1]}")

</template>

<script>

export default {
  name: 'SemiDonutChart',
  props: {
    series: {
      type: Array,
      default: () => [ 50, 70 ]
    },
    colors: {
      type: Array,
      default: () => [ '#d66f58', '#4ba5a5'] 
    },

    // Height should be half of width (ex: h: 50px; w: 100px)
    height: {
      type: Number,
      default: 65
    },

    // Width should be twice the height (ex: h: 50px; w: 100px)
    width: {
      type: Number,
      default: 130
    },
    symbol: {
      type: String,
      default: "%"
    },
    isLabels: {
      type: Boolean,
      default: true
    }

  }
}
</script>

<style lang="scss" scoped>

.semiDonutChart {
  .multi-graph {
    width: 100%;
    height: 100%;
    position: relative;
    color: #fff;
    font-size: 22px;
    font-weight: 600;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    overflow: hidden;
    box-sizing: border-box;

    .graph {
      width: 100%;
      height: 100%;
      border: 7px solid var(--fill);
      border-top: none;
      position: absolute;
      transform-origin: 50% 0% 0;
      border-radius: 0 0 130px 130px;
      left: 0;
      top: 100%;
      z-index: 5;
      animation: 1s fillGraphAnimation ease-in;
      transform: rotate(calc(1deg * (var(--percentage) * 1.8)));
      box-sizing: border-box;

      &:after {
        counter-reset: varible var(--percentage);
        background: var(--fill);
        box-sizing: border-box;
        border-radius: 2px;
        color: #fff;
        font-weight: 200;
        font-size: 12px;
        height: 20px;
        padding: 3px 5px;
        top: 0px;
        position: absolute;
        left: 0;
        transform: rotate(calc(-1deg * var(--percentage) * 1.8)) translate(-30px, 0px);
        transition: 0.2s ease-in;
        transform-origin: 0 50% 0;
        opacity: 0;
      }
    }

  }

  .graph__text {
    display: flex;
    justify-content: center;
    gap: 4px;
    font-size: 12px;
    color: gray;
    margin-bottom: 4px;
    width: 100%;

    .graph__description {
      display: flex;
      align-items: center;
      gap: 5px;
      margin: 2px 0;


      &-icon {
        height: 5px;
        width: 5px;
      }

      &-text {
        color: #999;
        font-size: 12px;
      }
    }
  }
}


</style>
