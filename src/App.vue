<template>
  <header>
  </header>

  <main>
    <div class="container-fluid" style="height: 100vh;">
      <div class="row h-100 ms-3">
        <MainPage
          @exportToPDF="exportToPDF"
        />
      </div>
    </div>
  </main>
</template>

<script>
import MainPage from './components/MainPage.vue';
import html2pdf from "html2pdf.js";
export default {
  components: {
  MainPage,
  },
  data() {
    return {
    }
  },
  methods: {
    // Convert to pdf
    exportToPDF() {
      html2pdf(document.getElementById("element-to-convert"), {
				margin: 2,
        filename: "myhtml.pdf",
			});
    },
  },
}
</script>

<style>
@import './assets/bootstrap.min.css';
main {
  margin: 0 auto;
  background-color: #fff;
}
</style>
