<template>
  <div class="popup">
    <div class="bbb" v-if="bbb[0]">
      <TheHeader />
      <TheTools />
    </div>
    <div class="nobbb" v-else>
      <h1>BBB not Detected</h1>
    </div>
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader.vue';
import TheTools from '@/components/TheTools.vue';

export default {
  name: 'App',
  components: {
    TheHeader,
    TheTools,
  },
  data() {
    return {
      bbb: false,
    };
  },
  methods: {
    checkBBB() {
      function DOMScript() {
        const check = document.getElementsByClassName('icon-bbb-group_chat')[0];
        return check != null;
      }
      chrome.tabs.executeScript({ code: `(${DOMScript})();` }, (results) => {
        this.bbb = results;
      });
    },
  },
  mounted() {
    this.checkBBB();
  },
};
</script>

<style>
html {
  width: 700px;
  height: 400px;
}
</style>
