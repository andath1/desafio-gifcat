<template>
  <div id="app">
    <div class="randon">
      <h1>Randon Gif Cat</h1>
    </div>
    <div class="container">
      <div class="form">
        <label>Titulo:</label>
        <input type="text" v-model="titulo" />
        <br />
        <br />
        <label>Filtro :</label>
        <select @change="cambiofiltro($event)">
          <option
            v-for="(filtro, index) in filtros"
            :key="index"
            :value="filtro"
            v-text="filtro"
          ></option>
        </select>
        <br />
        <br />
        <div class="row">
          <div class="col">
            <label>Color :</label>
            <select @change="cambiocolor($event)">
              <option
                v-for="(col, index) in colores"
                :key="index"
                :value="col.color"
                v-text="col.texto"
              ></option>
            </select>
            <br>
            <br>
          </div>
          <div class="col">
            <div class="circulo" :style="{ backgroundColor: color }"></div>
          </div>
        </div>
        <label>Tamaño :</label>
        <input v-model="tamano" type="number" />
      </div>
      <div class="imag">
        <button @click="obtenergato">Obtener mi gatito</button>
        <br />
        <img :src="imagen" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      filtros: ["blur", "mono", "sepia", "negative", "paint", "pixel"],
      colores: [
        {
          color: "blue",
          texto: "azul",
        },
        {
          color: "yellow",
          texto: "amarillo",
        },
        {
          color: "red",
          texto: "rojo",
        },
        {
          color: "green",
          texto: "verde",
        },
      ],
      titulo: "miau",
      filtro: "blur",
      color: "blue",
      tamaño: "300",
      imagen: "",
    };
  },
  methods: {
    obtenergato() {
      this.imagen = this.urlgatos;
    },
    cambiocolor(event) {
      this.color = event.target.value;
    },
    cambiofiltro(event) {
      this.filtro = event.target.value;
    },
  },
  computed: {
    urlgatos() {
      return `https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamano}`;
    },
  },
};
</script>

<style>
#app {
  margin-left: 250px;
  margin-top: 50px;
}
.form {
  background-color: rgb(241, 139, 139);
  width: 500px;
  padding-top: 20px;
  padding-bottom: 20px;
}
.randon {
  background-color: rgb(180, 196, 211);
  width: 500px;
  text-align: center;
  height: 70px;
  padding-top: 20px;
  color: rgb(12, 12, 92);
}
.circulo {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-left: 20px;
}
img {
  width: 170px;
  height: 170px;
}
 label {
  margin-left: 130px;
  margin-top: 20px;
} 
.imag {
  padding-top: 20px;
  background-color: rgb(180, 196, 211);
  width: 500px;
  height: 200px;
  text-align: center;
}
.col{
  display: inline-block;
}

</style>