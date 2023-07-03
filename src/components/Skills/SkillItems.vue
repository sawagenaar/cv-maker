<template>
  <div>
    <div class="mt-2 mb-1">{{ new_skill.skill }}</div>
    <div class="progress">
      <div class="progress-bar" role="progressbar"
        :style="{ width: `${new_skill.skillNiveau}%` }"
        aria-valuenow="{{ new_skill.skillNiveau }}"
        aria-valuemin="0" aria-valuemax="100"
      >
        {{ new_skill.skillNiveau }}
      </div>
    </div>
  </div>

</template>

<script>
export default {
  props: ['new_skill'],

}
</script>

<style scoped>
  .progress-bar {
    background-color: #6c757d;
  }
</style>