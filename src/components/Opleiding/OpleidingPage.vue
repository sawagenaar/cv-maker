<template>
  <h5 class="title text-center mt-3 fw-bold">Opleidingen</h5>
  <fieldset class="customize_fieldset">
    <form>
      <!-- Opleiding -->
      <div class="col">
        <label for="opleiding" class="form-label">Opleiding</label>
        <input
          class="form-control"
          type="text"
          id="opleiding"
          :value="opleiding"
          @input="$emit('update:opleiding', $event.target.value)"
        >
      </div>
      <!-- Instituut -->
      <div class="col">
        <label for="instituut" class="form-label">Instituut</label>
        <input
          class="form-control"
          type="text"
          id="instituut"
          :value="instituut"
          @input="$emit('update:instituut', $event.target.value)"
        >
      </div>

      <div class="row mt-2">
        <!-- Startdatum -->
        <div class="col">
          <label for="startMaandOpleiding">Startdatum</label>
        </div>
        <div class="col">
          <label for="endMaandOpleiding">Einddatum</label>
        </div>
        <div class="row m-0 p-0">
          <div class="col">
            <select
              class="form-select"
              id="startMaandOpleiding"
              name="startMaandOpleiding"
              :value="startMaandOpleiding"
              @input="$emit('update:startMaandOpleiding', $event.target.value)"
            >
              <option-month></option-month>
            </select>
          </div>
          <div class="col">
            <select
              class="form-select"
              id="startJaarOpleiding"
              name="startJaarOpleiding"
              :value="startJaarOpleiding"
              @input="$emit('update:startJaarOpleiding', $event.target.value)"
            >
              <option-jaar></option-jaar>
            </select>
          </div>
          <!-- Einddatum -->
          <div class="col">
            <select
              class="form-select"
              id="endMaandOpleiding"
              name="endMaandOpleiding"
              :value="endMaandOpleiding"
              @input="$emit('update:endMaandOpleiding', $event.target.value)"
            >
              <option-month></option-month>
            </select>
          </div>
          <div class="col">
            <select
              class="form-select"
              name="endJaarOpleiding"
              :value="endJaarOpleiding"
              @input="$emit('update:endJaarOpleiding', $event.target.value)"
            >
              <option-jaar></option-jaar>
            </select>
          </div>
        </div>
      </div>
      <div class="mt-3 d-flex justify-content-around">
        <button class="btn btn-secondary" @click.prevent="add_studieitem">Toevoegen</button>
        <button class="btn btn-secondary" @click.prevent="delete_studieitem">Verwijderen</button>
      </div>
    </form>
  </fieldset>
</template>

<script>
import OptionJaar from '../OptionJaar.vue';
import OptionMonth from '../OptionMonth.vue';
export default {
  components: { OptionJaar, OptionMonth },
  props: [
    'opleiding',
    'instituut',
    'startMaandOpleiding',
    'startJaarOpleiding',
    'endMaandOpleiding',
    'endJaarOpleiding'
  ],
  emits: [
    'update:opleiding',
    'update:instituut',
    'update:startMaandOpleiding',
    'update:startJaarOpleiding',
    'update:endMaandOpleiding',
    'update:endJaarOpleiding',
    'add_studieitem',
    'delete_studieitem'
  ],
  methods: {
    add_studieitem() {
      this.$emit('add_studieitem')
    },
    delete_studieitem(){
      this.$emit('delete_studieitem')
    }
  }
}
</script>

<style scoped>

</style>