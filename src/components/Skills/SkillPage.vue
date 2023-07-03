<template>
  <h5 class="title text-center mt-3 fw-bold">Vaardigheden</h5>
  <fieldset class="customize_fieldset">
    <form>
      <div class="row">
        <div class="col">
          <label for="skill" class="form-label">Vaardigheid</label>
          <input
            type="text"
            class="form-control"
            id="skill"
            :value="skill"
            @input="$emit('update:skill', $event.target.value)"
          >
        </div>
        <div class="col">
          <label for="skillNiveau" class="form-label">Niveau</label>
          <select
            class="form-select"
            id="skillNiveau"
            :value="skillNiveau"
            @input="$emit('update:skillNiveau', $event.target.value)"
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
        <button class="btn btn-secondary" @click.prevent="add_skill">Toevoegen</button>
        <button class="btn btn-secondary" @click.prevent="delete_skill">Verwijderen</button>
      </div>
    </form>
  </fieldset>
</template>

<script>
  export default {
    props: ['skill', 'skillNiveau'],
    emits: ['update:skill', 'update:skillNiveau', 'add_skill', 'delete_skill'],
    methods: {
      add_skill() {
        this.$emit('add_skill')
      },
      delete_skill(){
        this.$emit('delete_skill')
      }
  }
  }
</script>