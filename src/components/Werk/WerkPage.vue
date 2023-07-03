<template>
  <h5 class="title text-center mt-3 fw-bold">Werkervaring</h5>
  <fieldset class="customize_fieldset">
    <form>
      <div class="col">
        <label for="functie" class="form-label">Functie</label>
        <input
          class="form-control"
          type="text"
          id="functie"
          :value="functie"
          @input="$emit('update:functie', $event.target.value)"
        >
      </div>
      <div class="col">
        <label for="werkgever" class="form-label">Werkgever</label>
        <input
          class="form-control"
          type="text"
          id="werkgever"
          :value="werkgever"
          @input="$emit('update:werkgever', $event.target.value)"
        >
      </div>
      <div class="row mt-2">
        <!-- Startdatum -->
        <div class="col">
          <label for="startMaandWerk">Startdatum</label>
        </div>
        <div class="col">
          <label for="endMaandWerk">Einddatum</label>
        </div>
        <div class="row m-0 p-0">
          <div class="col">
            <select
              class="form-select"
              id="startMaandWerk"
              name="startMaandWerk"
              :value="startMaandWerk"
              @input="$emit('update:startMaandWerk', $event.target.value)"
            >
              <option-month></option-month>
            </select>
          </div>
          <div class="col">
            <select
              class="form-select"
              id="startJaarWerk"
              name="startJaarWerk"
              :value="startJaarWerk"
              @input="$emit('update:startJaarWerk', $event.target.value)"
            >
              <option-jaar></option-jaar>
            </select>
          </div>
          <!-- Einddatum -->
          <div class="col">
            <select
              class="form-select"
              id="endMaandWerk"
              name="endMaandWerk"
              :value="endMaandWerk"
              @input="$emit('update:endMaandWerk', $event.target.value)"
            >
              <option-month></option-month>
            </select>
          </div>
          <div class="col">
            <select
              class="form-select"
              name="endJaarWerk"
              :value="endJaarWerk"
              @input="$emit('update:endJaarWerk', $event.target.value)"
            >
              <option-jaar></option-jaar>
            </select>
          </div>
        </div>
      </div>
      <div class="mt-3 d-flex justify-content-around">
        <button class="btn btn-secondary" @click.prevent="add_werkitem">Toevoegen</button>
        <button class="btn btn-secondary" @click.prevent="delete_werkitem">Verwijderen</button>
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
    'functie',
    'werkgever',
    'startMaandWerk',
    'startJaarWerk',
    'endMaandWerk',
    'endJaarWerk'
  ],
  emits: [
    'update:functie',
    'update:werkgever',
    'update:startMaandWerk',
    'update:startJaarWerk',
    'update:endMaandWerk',
    'update:endJaarWerk',
    'add_werkitem',
    'delete_werkitem'
  ],
  methods: {
    add_werkitem() {
      this.$emit('add_werkitem')
    },
    delete_werkitem(){
      this.$emit('delete_werkitem')
    }
  }
}
</script>