<template>
  <div class="accordion-body">
    <div id="carouselControls" class="carousel carousel-dark slide" data-bs-ride="carousel" interval="false">
      <div class="carousel-inner">
        <div v-for="(slide, index) in this.slides" :class="index == 0 ? 'carousel-item active' : 'carousel-item'" :key="slide" style="border: 1px solid black">
          <img :src="slide" class="d-block w-100">
        </div>
      </div>
      <a class="carousel-control-prev" href="#carouselControls" role="button" v-if="navigation" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </a>
      <a class="carousel-control-next" href="#carouselControls" role="button" v-if="navigation" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </a>
    </div>
    <div class="row mt-2">
      <button type="button" @click="openSlide" class="btn btn-secondary col">Open in new Tab</button>
      <button type="button" class="btn btn-warning col" @click="navigation? navigation = false : navigation = true">{{navigation ? 'Hide Navgation' : 'Show Navigation'}}</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slides: [],
      navigation: true,
    };
  },
  methods: {
    openSlide() {
      window.open(document.querySelector('[class="carousel-item active"]').childNodes[0].getAttribute('src'));
    },
    init() {
      function DOMScript() {
        const PresentationLink = document.querySelectorAll('[clip-path="url(#viewBox)"]')[0].childNodes[0].childNodes[0].childNodes[1].getAttribute('xlink:href');
        return PresentationLink;
      }

      chrome.tabs.executeScript({ code: `(${DOMScript})();` }, (results) => {
        const link = results[0].substr(0, results[0].lastIndexOf('/'));
        const vm = this;

        function slideCounter(c) {
          const nLink = `${link}/${c}`;

          const req = new XMLHttpRequest();
          req.onreadystatechange = function () {
            if (req.readyState === 4) {
              if (req.status === 404 || req.status === 400 || req.status === 500) {
                return;
              }
              const count = c + 1;
              vm.slides.push(nLink.toString());
              slideCounter(count);
            }
          };
          req.open('GET', nLink, true);
          req.send();
        }
        slideCounter(1);
      });
      //  Carousel interval = false
      const myCarousel = document.querySelector('#carouselControls');
      const carousel = new bootstrap.Carousel(myCarousel, {
        interval: false,
        wrap: false,
      });
      console.log(carousel);
    },
  },
  mounted() {
    this.init();
  },
};
</script>
