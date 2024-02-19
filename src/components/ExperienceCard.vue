<template>
  <div
    class="experience-card"
    @click="toggleContent"
    @mouseenter="onMouseEnter"
    @mouseleave="onMouseLeave"
    :style="{ borderColor: currentBorderColor, backgroundColor: currentBgColor }"
  >
    <div class="center" v-if="!showAlternativeContent">
      <!-- Contenido principal -->
      <div class="image-container">
        <img :src="require(`@/assets/${experience.imageSrc}`)" :alt="experience.imageAlt">
      </div>
      <div class="text-year">
        <div class="year" :style="{ color: borderColor }">{{ experience.date }}</div>
      </div>
    </div>
    <div class="card-back" v-else>
      <!-- Contenido alternativo -->
      <h1>{{ titleCard }}</h1>
      <p :style="{ color: alternativeTextColor }">{{ alternativeText }}</p>
      <div class="tools">
        <p>Herramientas utilizadas</p>
        <div class="images">
          <img v-for="(tool, toolIndex) in experience.tools" :key="toolIndex" :src="require(`@/assets/${tool}`)" alt="nada">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['experience', 'backgroundColor', 'borderColor', 'titleCard', 'alternativeTextColor', 'alternativeText'],
  data() {
    return {
      showAlternativeContent: false,
      currentBorderColor: this.borderColor,
      currentBgColor: this.backgroundColor,
      alternativeBorderColor: '#6D6D6D', // Cambia aquí al color que desees
    };
  },
  methods: {
    onMouseEnter() {
      if (!this.showAlternativeContent) {
        this.currentBorderColor = this.alternativeBorderColor;
        this.currentBgColor = this.backgroundColor;
        this.showAlternativeContent = !this.showAlternativeContent;
        this.updateStyles();
      }
    },
    onMouseLeave() {
      if (this.showAlternativeContent) {
        this.currentBorderColor = this.borderColor;
        this.currentBgColor = this.backgroundColor;
        this.showAlternativeContent = !this.showAlternativeContent;
        this.updateStyles();
      }
    },
    updateStyles() {
      this.currentBorderColor = this.showAlternativeContent
        ? this.alternativeBorderColor
        : this.borderColor;
      this.currentBgColor = this.showAlternativeContent
        ? this.alternativeColor
        : this.backgroundColor;
    },
  },
};
</script>

<style>
.experience-card {
  width: 400px;
  height: 600px;
  border: 5px solid;
  background-color: #373737;
  color: #FFF;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition: background-color 0.1s;
}

.center {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.image-container {
  height: 550px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.experience-card img {
  width: 80%;
  height: auto;
  border-radius: 5px;
}

.year {
  font-size: 20px;
  color: #F07F36;
  font-weight: bold;
}

.card-back{
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: justify;
  flex-direction: column;
  padding: 30px;
}

.images{
  display: flex;
  align-content: space-between;
}

.tools{
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tools img{
  width: auto;
  height: 30px;
}

@media screen and (max-width:880px){
  .experience-card{
    margin-bottom: 20px;
  }
}

</style>
