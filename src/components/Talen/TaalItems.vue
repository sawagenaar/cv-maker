<template>
  <div>
    <div class="mt-2 mb-1">{{ new_taal.taal }}</div>
    <div class="progress">
      <div class="progress-bar" role="progressbar"
        :style="{ width: `${new_taal.taalNiveau}%` }"
        aria-valuenow="{{ new_taal.taalNiveau }}"
        aria-valuemin="0" aria-valuemax="100"
      >
        {{ new_taal.taalNiveau }}
      </div>
    </div>
  </div>

</template>

<script>
export default {
  props: ['new_taal'],

}
</script>

<style scoped>
  .progress-bar {
    background-color: #6c757d;
  }
</style>