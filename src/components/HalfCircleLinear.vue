<template>
  <div class="component">
    <div class="role">{{role}}</div>
    <div class="linear-graph">
      <svg class="half-circle" width="20" height="20" :style="{ left: centered(weighted(userScore)) }">
        <path d="m 1 8 a 1 1 0 0 1 15 0" fill="blue" stroke="gray" stroke-width="1" />
      </svg>
      <svg :width="weighted(max)">
        <line :x1="weighted(min)" y1="0" :x2="weighted(min)" y2="16" stroke="gray" stroke-width="1" />
        <line :x1="weighted(min)" y1="8" :x2="weighted(max)" y2="8" stroke="gray" stroke-width="1" />
        <line :x1="weighted(max)" y1="0" :x2="weighted(max)" y2="16" stroke="gray" stroke-width="1" />
      </svg>
      <svg class="half-circle" width="20" height="20" :style="{ left: centered(weighted(suggestedScore)) }">
        <path d="m 1 8 a 1 1 0 0 0 15 0" fill="cyan" stroke="gray" stroke-width="1" />
      </svg>
    </div>
    <svg class="circle" width="20" height="20">
      <circle cx="9" cy="9" r="8" :stroke="stroke()" stroke-width="1" :fill="fill()" />
      <path v-if="stroke()==='white'" d="m 1 9 a 1 1 0 0 0 15 0" fill="white" stroke="white" stroke-width="1" />
    </svg>
    <div class="your-average">{{yourAverage()}}</div>
    <div class="team-average">{{teamAverage()}}</div>
  </div>
</template>

<script>
export default {
  props: [
    'role',
    'min',
    'max',
    'userScore',
    'suggestedScore',
  ],

  methods: {
    weighted(val) {
      return val * 100;
    },

    centered(val) {
      return val - 9;
    },
    yourAverage() {
      const val = (parseFloat(this.userScore) + parseFloat(this.suggestedScore)) / 2;
      return val.toFixed(2);
    },
    teamAverage() {
      const val = (parseFloat(this.min) + parseFloat(this.max)) / 2;
      return val.toFixed(2);
    },
    stroke() {
      const diff = parseFloat(this.yourAverage()) - parseFloat(this.teamAverage()); 
      if (diff > 0.5) {
        return 'red';
      } else if (diff < 0.5) {
        return 'green';
      } else {
        return 'white';
      }
    },
    fill() {
      const diff = parseFloat(this.yourAverage()) - parseFloat(this.teamAverage()); 
      if (diff > 0.5) {
        return 'red';
      } else if (diff < 0.5) {
        return 'green';
      } else {
        return 'none';  
      }
    },
  }
}
</script>

<style lang="scss">
  .component {
    display: flex;
    height: 40px;

    .role {
      width: 350px;
    }
    .linear-graph {
      width: 570px;
    }
    .half-circle {
      position: absolute;
      margin-left: 350px;
    }
    .your-average {
      width: 100px;
      margin-left: 5px;
    }
    .team-average {
      width: 100px;
    }
  }
</style>
