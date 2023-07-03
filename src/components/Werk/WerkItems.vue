<template>
  <div class="row px-3 mt-2">
    <div class="col-6 text-break">{{ werk.functie }}</div>
    <div class="col-6 small">{{ werk.startMaandWerk }} {{ werk.startJaarWerk }} - {{ werk.endMaandWerk }} {{ werk.endJaarWerk }}</div>
  </div>
  <div class="row px-3">
    <div class="col text-break">{{ werk.werkgever }}</div>
  </div>
</template>

<script>
export default {
  props: ['werk'],
}
</script>