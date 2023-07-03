<template>
  <h5 class="title text-center mt-3 fw-bold">Personalia</h5>
  <div class="row mt-4">
    <!-- foto -->
    <div class="col-2">
      <form>
        <div class="form-group" v-if="!image">
          <label for="formFile" role="button" class="form-label text-center">
            <p class="text-center">Foto</p>
            <p><img class="foto" src="../assets/img/images.jfif" alt="foto"></p>
          </label>
          <input class="form-control d-none" type="file" id="formFile" @change="onFileChange">
        </div>
        <img v-else class="foto" :src="image" />
        <button v-if="image" @click="removeImage" class="btn btn-link mybtn">Remove image</button>
      </form>
    </div>
    <!--  -->
    <div class="col ps-5">
      <form>
        <!-- Voornaam en achternaam -->
        <div class="row">
          <div class="col">
            <label for="naam" class="form-label">Voornaam</label>
            <input
              class="form-control"
              type="text"
              id="naam"
              :value="naam"
              @input="$emit('update:naam', $event.target.value)"
            >
          </div>
          <div class="col">
            <label for="achternaam" class="form-label">Achternaam</label>
            <input
              class="form-control"
              type="text"
              id="achternaam"
              :value="achternaam"
              @input="$emit('update:achternaam', $event.target.value)"
            >
          </div>
        </div>
        <!-- Email -->
        <div class="row mt-1">
          <div class="col">
            <label for="email" class="form-label">E-mail</label>
            <input
              class="form-control"
              type="email"
              id="email"
              :value="email"
              @input="$emit('update:email', $event.target.value)"
            >
          </div>
        </div>
      </form>
    </div>
    <form>
      <!-- Telefon -->
      <div class="col">
        <label for="telefoon" class="form-label">Telefoonnummer</label>
        <input
          class="form-control"
          type="tel"
          id="telefoon"
          :value="telefoon"
          @input="$emit('update:telefoon', $event.target.value)"
        >
      </div>
      <!-- Adres -->
      <div class="col">
        <label for="adres" class="form-label">Adres</label>
        <input
          class="form-control"
          type="text"
          id="adres"
          :value="adres"
          @input="$emit('update:adres', $event.target.value)"
        >
      </div>
      <div class="row mt-1">
        <!-- Postcode -->
        <div class="col">
          <label for="postcode" class="form-label">Postcode</label>
          <input
            class="form-control"
            type="text"
            id="postcode"
            :value="postcode"
            @input="$emit('update:postcode', $event.target.value)"
          >
        </div>
        <!-- Plaats -->
        <div class="col">
          <label for="plaats" class="form-label">Plaats</label>
          <input
            class="form-control"
            type="text"
            id="plaats"
            :value="plaats"
            @input="$emit('update:plaats', $event.target.value)"
          >
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ['naam', 'achternaam', 'image', 'email', 'telefoon', 'adres', 'postcode', 'plaats'],
  emits: ['update:naam', 'update:achternaam', 'update:email', 'update:telefoon',
    'update:adres', 'update:postcode', 'update:plaats', 'on-file-change', 'remove-image'],
  methods: {
    onFileChange(e) {
      this.$emit('on-file-change', e);
    },
    removeImage() {
      this.$emit('remove-image');
    }
  }
}
</script>

<style scoped>
.foto {
  max-width: 6em;
  width: 5.2em;
}
.mybtn {
  font-size: 0.6rem;
  line-height: 1;
  color: black;
}
</style>