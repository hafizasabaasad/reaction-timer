<template>
  <p>Reaction Time: {{ score }} ms</p>
  <p class="rank">
    {{ rank }}
  </p>

  <!-- fast -->
  <span v-if="reaction === 'fast'" class="material-symbols-outlined icon">
    sentiment_very_satisfied
  </span>
  <!-- medium -->
  <span v-if="reaction === 'medium'" class="material-symbols-outlined icon">
    sentiment_satisfied
  </span>
  <!-- slow reaction -->
  <span v-if="reaction === 'slow'" class="material-symbols-outlined icon">
    sentiment_very_dissatisfied
  </span>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
      reaction: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Awesome! 'You have Ninja Fingers'";
      this.reaction = "fast";
    } else if (this.score < 400) {
      this.rank = "Great work! 'Rapid Reflexes'";
      this.reaction = "medium";
    } else {
      this.rank = "Keep trying:( 'Snail pace....'";
      this.reaction = "slow";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: rgb(33, 171, 171);
  font-weight: bold;
}
/* Option 2 */
.icon {
  font-size: 80px;
}
</style>
