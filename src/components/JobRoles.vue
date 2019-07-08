<template>
  <div class="container">
    <header>
      <div class="role-header">Job Role: {{jobRole}}</div>
      <div class="score-header">0</div>
      <div class="score-header">1</div>
      <div class="score-header">2</div>
      <div class="score-header">3</div>
      <div class="score-header">4</div>
      <div class="score-header">5</div>
      <div class="average-header">Your avg</div>
      <div class="average-header">Tribe avg</div>
    </header>
    <svg class="lines" width="1000" height="1000">
      <line x1="50" y1="0" x2="50" y2="1000" stroke="gray" stroke-dasharray="3" stroke-width="1" />
      <line x1="150" y1="0" x2="150" y2="1000" stroke="gray" stroke-dasharray="3" stroke-width="1" />
      <line x1="250" y1="0" x2="250" y2="1000" stroke="gray" stroke-dasharray="3" stroke-width="1" />
      <line x1="350" y1="0" x2="350" y2="1000" stroke="gray" stroke-dasharray="3" stroke-width="1" />
      <line x1="450" y1="0" x2="450" y2="1000" stroke="gray" stroke-dasharray="3" stroke-width="1" />
      <line x1="550" y1="0" x2="550" y2="1000" stroke="gray" stroke-dasharray="3" stroke-width="1" />
    </svg>
    <div class="scores">
      <div v-for="(item, index) in graphData" :key="index">
        <HalfCircleLinear
          :role="item.role"
          :min="item.min"
          :max="item.max"
          :userScore="item.userScore"
          :suggestedScore="item.suggestedScore">
        </HalfCircleLinear>
      </div>
    </div>
  </div>
</template>

<script>
import HalfCircleLinear from '@/components/HalfCircleLinear';

export default {
  components: {
    HalfCircleLinear,
  },
  data: () => {
    return {
      jobRole: 'Designer',
      graphData: [
        { role: 'Visual Design', min: '0.5', max: '3.5', userScore: '3', suggestedScore: '2' },
        { role: 'Artificial Intelligence', min: '0', max: '2.5', userScore: '0', suggestedScore: '2' },
        { role: 'Design Facilitator', min: '0.5', max: '4', userScore: '1', suggestedScore: '2' },
        { role: 'Infrastructure Service Delivery', min: '0.5', max: '3.5', userScore: '1', suggestedScore: '3' },
        { role: 'Squad Leadership', min: '1', max: '4.5', userScore: '0', suggestedScore: '4' }, 
        { role: 'Editorial & Content', min: '0', max: '2', userScore: '0', suggestedScore: '4' },
        { role: 'Offering Management', min: '2.5', max: '5', userScore: '2', suggestedScore: '4' },
        { role: 'Change Management', min: '0.5', max: '2.5', userScore: '1', suggestedScore: '3' },
        { role: 'Software Development', min: '0.5', max: '3.5', userScore: '1', suggestedScore: '4' },
        { role: 'Business Analysis', min: '1', max: '3', userScore: '1', suggestedScore: '4' },
        { role: 'User Experience Design', min: '0', max: '2', userScore: '1', suggestedScore: '0' },
        { role: 'UXD Architecture', min: '1.5', max: '3.5', userScore: '1', suggestedScore: '4' },
      ]
    }
  },
}
</script>
<style lang="scss">
  header {
    padding: 0 0 20px;
    border-bottom: solid 1px gray;

    div {
      display: inline-block;
    }
    .role-header {
      width: 300px;
    }
    .score-header, .average-header {
      text-align: center;
      width: 100px;
    }
  }
  .lines {
    position: absolute;
    margin-left: 300px;
  }
  .scores {
    margin-top: 20px;
    display: inline-block;
    position: absolute;
  }
</style>
