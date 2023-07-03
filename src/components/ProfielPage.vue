<template>
  <h5 class="title text-center mt-3 fw-bold">Profiel</h5>
  <label for="textarea" class="form-label">Omschrijving</label>
  <textarea
    class="form-control"
    rows="3"
    id="textarea"
    :value="profiel"
    @input="$emit('update:profiel', $event.target.value)"
  ></textarea>
</template>

<script>
  export default {
    props: ['profiel'],
    emits: ['update:profiel']
  }
</script>