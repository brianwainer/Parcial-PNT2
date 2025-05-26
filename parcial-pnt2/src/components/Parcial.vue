<template>
  <div class="text-transformer">
    <form @submit.prevent>
      <div class="form-group">
        <label for="inputText">Ingrese un texto:</label>
        <input 
          type="text" 
          id="inputText"
          v-model="inputText"
          class="form-control"
          placeholder="Ingrese un texto..."
        >
      </div>

      <div class="results mt-4">
        <p>Cantidad de caracteres: {{ contadorCaracteres }}</p>
        
        <h3>Transformaciones:</h3>
        <ol>
          <li>Codificado: {{ textoCodificado }}</li>
          <li>Mayúsculas: {{ textoMayusculas }}</li>
          <li>Minúsculas: {{ textoMinusculas }}</li>
          <li>Alternado (inicio mayúscula): {{ textoAlternadoMayuscula }}</li>
          <li>Alternado (inicio minúscula): {{ textoAlternadoMinuscula }}</li>
        </ol>
      </div>
    </form>

    <div class="answers mt-5">
      <h3>Respuestas:</h3>
      <p class="answer-text">
        1 = C, 2 = C, 3 = A
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ParcialTransformer',
  data() {
    return {
      inputText: ''
    }
  },
  computed: {
    contadorCaracteres() {
      return this.inputText.length
    },
    
    textoCodificado() {
      return this.inputText.toLowerCase().split('').map(char => {
        switch(char) {
          case 'a': return 'u'
          case 'e': return 'o'
          case 'o': return 'e'
          case 'u': return 'a'
          default: return char
        }
      }).join('')
    },
    
    textoMayusculas() {
      return this.inputText.toUpperCase()
    },
    
    textoMinusculas() {
      return this.inputText.toLowerCase()
    },
    
    textoAlternadoMayuscula() {
      return this.inputText.split('').map((char, index) => 
        index % 2 === 0 ? char.toUpperCase() : char.toLowerCase()
      ).join('')
    },
    
    textoAlternadoMinuscula() {
      return this.inputText.split('').map((char, index) => 
        index % 2 === 0 ? char.toLowerCase() : char.toUpperCase()
      ).join('')
    }
  }
}
</script>

<style scoped>
.text-transformer {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.form-control {
  width: 100%;
  padding: 8px;
  margin: 10px 0;
}

.results {
  text-align: left;
}

ol {
  padding-left: 20px;
}

li {
  margin: 10px 0;
}

.answers {
  margin-top: 40px;
  text-align: left;
  border-top: 1px solid #ccc;
  padding-top: 20px;
}

.answer-text {
  font-weight: bold;
  color: #2c3e50;
}
</style>
