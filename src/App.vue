<template>
  <div id="app">
    <div id="form">
      <div class="input--group">
        <label for="backgroundColor">Color de Fondo:</label>
        <input id="backgroundColor" type="text" v-model="backgroundColor">
      </div>
      <div class="input--group">
        <label for="textColor">Color de Texto:</label>
        <input id="textColor" type="text" v-model="textColor">
      </div>
      <div>
        <label for="showText">Mostrar texto</label>
        <input id="showText" type="checkbox" v-model="showText" />
      </div>
      <div class="input--group">
        <label for="borderRange">Borde</label>
        <input id="borderRange" type="range" v-model="borderRange" min="0" max="20" />
      </div>
      <div class="input--group">
        <label for="textArea">Contenido textual</label>
        <textarea id="textArea" rows="2" v-model="textArea"></textarea>
      </div>
      <div class="input--group">
        <label for="fontText">Tipografía:</label>
        <select id="fontText" v-model="fontText">
          <option v-for="font in fonts" :key="font" :value="font">{{ font }}</option>
        </select>
      </div>
      <div>
        <label for="opacityBox">Opaco</label>
        <input id="opacityBox" type="checkbox" v-model="opacityBox" />
      </div>
      <div class="input--group">
        <label>Radio de borde</label>
        <div>
          <input id="sizeSmall" type="radio" value="small" v-model="borderRadius" /> Pequeño
          <input id="sizeMedium" type="radio" value="medium" v-model="borderRadius" /> Mediano
          <input id="sizeLarge" type="radio" value="large" v-model="borderRadius" /> Grande
        </div>
      </div>
    </div>
    <div id="presentationCard" :class="{ 'opacityBox': opacityBox }" :style="{
      backgroundColor: backgroundColor,
      color: textColor,
      border: borderRange + 'px solid orange',
      fontFamily: fontText,
      borderRadius: borderRadius === 'small' ? '5px' : (borderRadius === 'medium' ? '10px' : '15px')
    }">
      <p v-if="showText">{{ textArea }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      backgroundColor: '',
      textColor: '',
      showText: false,
      borderRange: 0,
      textArea: '',
      fontText: 'Arial',
      opacityBox: false,
      borderRadius: 'medium',
      fonts: ['Arial', 'Helvetica', 'Times New Roman', 'Courier New']
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: grid;
  grid-template-columns: 50% 50%;
  padding: 1rem 4rem;
  gap: 1rem;
}

#form {
  background-color: darkcyan;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: start;
  padding: 2rem;
}

#presentationCard {
  background-color: #f1f1f1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

.opacityBox {
  opacity: 0.5;
}

.input--group {
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: start;
  margin: 0.5rem 0;
}

input[type="text"],
input[type="range"],
select,
textarea {
  width: 100%;
}

input[type="radio"] {
  margin: 0 0.5rem;
}
</style>
