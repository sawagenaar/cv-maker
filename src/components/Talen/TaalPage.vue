<template>
  <h5 class="title text-center mt-3 fw-bold">Talen</h5>
  <fieldset class="customize_fieldset">
    <form>
      <div class="row">
        <div class="col">
          <label for="taal" class="form-label">Taal</label>
          <input
            type="text"
            class="form-control"
            id="taal"
            :value="taal"
            @input="$emit('update:taal', $event.target.value)"
          >
        </div>
        <div class="col">
          <label for="taalNiveau" class="form-label">Niveau</label>
          <select
            class="form-select"
            id="taalNiveau"
            :value="taalNiveau"
            @input="$emit('update:taalNiveau', $event.target.value)"
          >
            <option value="" selected>Maak een keuze</option>
            <option value="20">Beginner</option>
            <option value="40">Redelijk</option>
            <option value="60">Goed</option>
            <option value="80">Zeer goed</option>
            <option value="100">Uitstekend</option>
          </select>
        </div>
      </div>
      <div class="mt-3 d-flex justify-content-around">
        <button class="btn btn-secondary" @click.prevent="add_taal">Toevoegen</button>
        <button class="btn btn-secondary" @click.prevent="delete_taal">Verwijderen</button>
      </div>
    </form>
  </fieldset>
</template>

<script>
  export default {
    props: ['taal', 'taalNiveau'],
    emits: ['update:taal', 'update:taalNiveau', 'add_taal', 'delete_taal'],
    methods: {
      add_taal() {
        this.$emit('add_taal')
      },
      delete_taal(){
        this.$emit('delete_taal')
      }
  }
  }
</script>