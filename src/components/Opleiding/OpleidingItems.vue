<template>
  <div class="row px-3 mt-2">
    <div class="col-6 text-break">{{ studie.opleiding }}</div>
    <div class="col-6 small">{{ studie.startMaandOpleiding }} {{ studie.startJaarOpleiding }} - {{ studie.endMaandOpleiding }} {{ studie.endJaarOpleiding }}</div>
  </div>
  <div class="row px-3">
    <div class="col text-break">{{ studie.instituut }}</div>
  </div>
</template>

<script>
export default {
  props: ['studie'],
}
</script>