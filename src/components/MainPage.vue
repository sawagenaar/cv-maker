<template>
  <div class="anketa col-md h-100 overflow-auto">
    <!-- Personalia -->
    <prive-page
      v-model:naam="naam"
      v-model:achternaam="achternaam"
      :image="image"
      @on-file-change="onFileChange"
      @remove-image="removeImage"
      v-model:email="email"
      v-model:telefoon="telefoon"
      v-model:adres="adres"
      v-model:postcode="postcode"
      v-model:plaats="plaats"
    ></prive-page>

    <!-- Profiel -->
    <profiel-page
      v-model:profiel="profiel"
    ></profiel-page>

    <!-- Opleidingen -->
    <opleiding-page
      v-model:opleiding="new_studie.opleiding"
      v-model:instituut="new_studie.instituut"
      v-model:startMaandOpleiding="new_studie.startMaandOpleiding"
      v-model:startJaarOpleiding="new_studie.startJaarOpleiding"
      v-model:endMaandOpleiding="new_studie.endMaandOpleiding"
      v-model:endJaarOpleiding="new_studie.endJaarOpleiding"
      @add_studieitem="add_studieitem"
      @delete_studieitem="delete_studieitem"
    >
    </opleiding-page>

    <!-- Werkervaring -->
    <werk-page
      v-model:functie="new_werkitem.functie"
      v-model:werkgever="new_werkitem.werkgever"
      v-model:startMaandWerk="new_werkitem.startMaandWerk"
      v-model:startJaarWerk="new_werkitem.startJaarWerk"
      v-model:endMaandWerk="new_werkitem.endMaandWerk"
      v-model:endJaarWerk="new_werkitem.endJaarWerk"
      @add_werkitem="add_werkitem"
      @delete_werkitem="delete_werkitem"
    ></werk-page>

    <!-- Talen -->
    <taal-page
      v-model:taal="new_taal.taal"
      v-model:taalNiveau="new_taal.taalNiveau"
      @add_taal="add_taal"
      @delete_taal="delete_taal"
    ></taal-page>

    <!-- Vaardigheden -->
    <skill-page
      v-model:skill="new_skill.skill"
      v-model:skillNiveau="new_skill.skillNiveau"
      @add_skill="add_skill"
      @delete_skill="delete_skill"
    ></skill-page>

  </div>
  <!--Resultaat  -->
  <div class="col-md h-100 overflow-auto ms-3 mt-3" id="element-to-convert">
    <div class="row">
      <!-- sidebar -->
      <div class="col-4 ms-2">
        <!-- Image -->
        <img class="image" :src="image"/>
        <!-- Email -->
        <div class="mt-4">
          <img v-if="email" src="../assets/img/email.svg"/>&nbsp;
          <small class="text-break"> {{ email }} </small>
        </div>
        <!-- Telefoon -->
        <div>
          <img v-if="telefoon" src="../assets/img/tel.svg"/>&nbsp;
          <small class="text-break"> {{ telefoon }}</small>
        </div>
        <!-- Adres -->
        <div>
          <img v-if="adres" src="../assets/img/adres.svg"/>&nbsp;
          <small class="text-break"> {{ adres }}</small>
          <p><small class="text-break"> {{ postcode }} {{ plaats }}</small></p>
        </div>
        <!-- Talen -->
        <div>
          <h5 v-if="talen.length" class="title text-center fw-bold pt-3">Talen</h5>
          <taal-items :key="index" :new_taal="taal" v-for="(taal, index) in talen"></taal-items>
        </div>
        <!-- Vaardiheden -->
        <div>
          <h5 v-if="skills.length" class="title text-center fw-bold pt-3">Vaardigheden</h5>
          <skill-items :key="index" :new_skill="skill" v-for="(skill, index) in skills"></skill-items>
        </div>
      <!-- end sidebar -->
      </div>
      <!-- delimiter -->
      <div class="vr"></div>
      <!-- main column -->
      <div class="col">
        <!-- Naam, achternaam -->
        <h3 class="text-center mt-1 fw-bold text-break">{{ naam }} {{ achternaam }}</h3>
        <!-- Profiel -->
        <h5 v-show="profiel" class="title text-center fw-bold pt-3">Profiel</h5>
        <p class="text-break"> {{ profiel }} </p>
        <!-- Opleidingen -->
        <h5 v-if="studieitems.length" class="title text-center fw-bold pt-3">Opleidingen</h5>
        <opleiding-items :key="index" :studie="studieitem" v-for="(studieitem, index) in studieitems"></opleiding-items>
        <!-- Werkervaring -->
        <h5 v-if="werkitems.length" class="title text-center fw-bold pt-3">Werkervaring</h5>
        <werk-items :key="index" :werk="werkitem" v-for="(werkitem, index) in werkitems"></werk-items>
      <!-- end main column -->
      </div>
    </div>
  </div>
  <div>
    <!-- Convert to pdf -->
    <button class="btn btn-secondary position-fixed bottom-0 end-0" @click="exportToPDF">Downloaden</button>
  </div>
</template>

<script>
import PrivePage from './PrivePage.vue';
import ProfielPage from './ProfielPage.vue';
import TaalPage from './Talen/TaalPage.vue';
import TaalItems from './Talen/TaalItems.vue';
import SkillPage from './Skills/SkillPage.vue';
import SkillItems from './Skills/SkillItems.vue';
import OpleidingItems from './Opleiding/OpleidingItems.vue';
import OpleidingPage from './Opleiding/OpleidingPage.vue';
import WerkItems from './Werk/WerkItems.vue';
import WerkPage from './Werk/WerkPage.vue';

export default {
  components: {
    TaalPage,
    TaalItems,
    SkillPage,
    SkillItems,
    WerkItems,
    PrivePage,
    OpleidingPage,
    WerkPage,
    OpleidingItems,
    ProfielPage
  },
  emits: ['exportToPDF'],
  data() {
    return {
      naam: '',
      achternaam: '',
      email: '',
      image: null,
      telefoon: '',
      adres: '',
      postcode: '',
      plaats: '',
      profiel: '',
      // Opleiding data
      studieitems: [],
      new_studie: {
        opleiding: '',
        instituut: '',
        startMaandOpleiding: '',
        startJaarOpleiding: '',
        endMaandOpleiding: '',
        endJaarOpleiding: '',
      },
      // Werk data
      werkitems: [],
      new_werkitem: {
        functie: '',
        werkgever: '',
        startMaandWerk: '',
        startJaarWerk: '',
        endMaandWerk: '',
        endJaarWerk: '',
      },
      // Talen data
      talen: [],
      new_taal: {
        taal: '',
        taalNiveau: '',
      },
      // Vaardigheden data
      skills: [],
      new_skill: {
        skill: '',
        skillNiveau: '',
      },
    }
  },
  methods: {
    // Foto
    onFileChange(e) {
      var files = e.target.files || e.dataTransfer.files;
      if (!files.length)
        return;
      this.createImage(files[0]);
    },
    createImage(file) {
      var image = new Image();
      var reader = new FileReader();
      var vm = this;
      reader.onload = (e) => {
        vm.image = e.target.result;
      };
      reader.readAsDataURL(file);
    },
    removeImage: function () {
      this.image = '';
    },
    // Add werk
    add_werkitem(){
      if(this.new_werkitem.functie != ''){
        this.werkitems.push({
          functie: this.new_werkitem.functie,
          werkgever: this.new_werkitem.werkgever,
          startMaandWerk: this.new_werkitem.startMaandWerk,
          startJaarWerk: this.new_werkitem.startJaarWerk,
          endMaandWerk: this.new_werkitem.endMaandWerk,
          endJaarWerk: this.new_werkitem.endJaarWerk,
        });
        this.new_werkitem.functie='';
        this.new_werkitem.werkgever='';
        this.new_werkitem.startMaandWerk='';
        this.new_werkitem.startJaarWerk='';
        this.new_werkitem.endMaandWerk='';
        this.new_werkitem.endJaarWerk='';
      }
    },
    // Delete werk
    delete_werkitem(id){
      this.werkitems.pop(id,1);
    },
    // Add opleiding
    add_studieitem(){
      if(this.new_studie.opleiding != ''){
        this.studieitems.push({
          opleiding: this.new_studie.opleiding,
          instituut: this.new_studie.instituut,
          startMaandOpleiding: this.new_studie.startMaandOpleiding,
          startJaarOpleiding: this.new_studie.startJaarOpleiding,
          endMaandOpleiding: this.new_studie.endMaandOpleiding,
          endJaarOpleiding: this.new_studie.endJaarOpleiding,
        });
        this.new_studie.opleiding='';
        this.new_studie.instituut='';
        this.new_studie.startMaandOpleiding='';
        this.new_studie.startJaarOpleiding='';
        this.new_studie.endMaandOpleiding='';
        this.new_studie.endJaarOpleiding='';
      }
    },
    // Delete opleiding
    delete_studieitem(id){
      this.studieitems.pop(id,1);
    },
    // Add taal
    add_taal(){
      if(this.new_taal.taal != '') {
        this.talen.push({
          taal: this.new_taal.taal,
          taalNiveau: this.new_taal.taalNiveau,
        });
      }
      this.new_taal.taal='';
      this.new_taal.taalNiveau='';
    },
    // Delete taal
    delete_taal(id){
      this.talen.pop(id,1);
    },
    // Add vaardigheid
    add_skill(){
      if(this.new_skill.skill != '') {
        this.skills.push({
          skill: this.new_skill.skill,
          skillNiveau: this.new_skill.skillNiveau,
        });
      }
      this.new_skill.skill='';
      this.new_skill.skillNiveau='';
    },
    // Delete vaardigheid
    delete_skill(id){
      this.skills.pop(id,1);
    },
    // Сonvert to pdf
    exportToPDF() {
      this.$emit('exportToPDF');
    }
  }
}
</script>

<style scoped>
.image {
  width: 100%;
}
.vr {
  margin: 0;
  padding: 0;
  height: 280mm;
}
svg {
  width: 10px;
}
</style>
