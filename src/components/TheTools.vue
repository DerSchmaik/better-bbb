<template>
  <div class="accordion accordion-flush" style="width: 700px"  id="accordionFlush">
    <!-- Info -->
    <div class="accordion-item">
      <h2 class="accordion-header" id="flush-headingInfo">
        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseInfo" aria-expanded="false" aria-controls="flush-collapseInfo">
          Information
        </button>
      </h2>
      <div id="flush-collapseInfo" class="accordion-collapse collapse" aria-labelledby="flush-headingInfo" data-bs-parent="#accordionFlush">
        <the-info-tool />
      </div>
    </div>
    <!-- Presentation Tools -->
    <div class="accordion-item">
      <h2 class="accordion-header" id="flush-headingPrTools">
        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapsePrTools" aria-expanded="false" aria-controls="flush-collapsePrTools">
          Presentation Tools
        </button>
      </h2>
      <div id="flush-collapsePrTools" class="accordion-collapse collapse" aria-labelledby="flush-headingPrTools" data-bs-parent="#accordionFlush">
        <the-presentation-tool />
      </div>
    </div>
    <!-- Chat Tools -->
    <div class="accordion-item">
      <h2 class="accordion-header" id="flush-headingChatTools">
        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseChatTools" aria-expanded="false" aria-controls="flush-collapseChatTools">
          Chat Tools
        </button>
      </h2>
      <div id="flush-collapseChatTools" class="accordion-collapse collapse" aria-labelledby="flush-headingChatTools" data-bs-parent="#accordionFlush">
        <h4>comming soon...</h4>
      </div>
    </div>
    <!-- Theme Manager -->
    <div class="accordion-item">
      <h2 class="accordion-header" id="flush-headingThemeManager">
        <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseThemeManager" aria-expanded="false" aria-controls="flush-collapseThemeManager">
          Theme Manager
        </button>
      </h2>
      <div id="flush-collapseThemeManager" class="accordion-collapse collapse" aria-labelledby="flush-headingThemeManager" data-bs-parent="#accordionFlush">
        <h4>comming soon...</h4>
      </div>
    </div>
  </div>
</template>

<script>
import TheInfoTool from './TheInfoTool.vue';
import ThePresentationTool from './ThePresentationTool.vue';

export default {
  components: {
    ThePresentationTool,
    TheInfoTool,
  },
};
</script>
