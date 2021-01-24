<template>
  <div id="app">
    <div class="row">
      <div class="col-6">
        <div class="container">
          <div class="alert alert-dismissible alert-primary">
            <button type="button" class="close" data-dismiss="alert">&times;</button>
            <strong>{{msg}}</strong>
          </div>
          <form name="nuevaNota" @submit.prevent="agregarNota">
            <div class="form-group">
              <label for="noteTitle">Título de la Nota</label>
              <input type="text" class="form-control" v-model="nota.titulo" maxlength="30" required>
              <small id="emailHelp" class="form-text text-muted">Máximo de 30 caracteres.</small>
            </div>
            <div class="form-group">
              <label for="noteText">Nota</label>
              <textarea class="form-control" v-model="nota.texto" required></textarea>
            </div>
            <button type="submit" class="btn btn-success">Guardar Nota</button>
          </form>
        </div>
      </div>
      <div class="col-6">
        <div class="card bg-light mb-3" style="max-width: 20rem;" v-for="(nota, index) in notas">
          <div class="card-header">{{nota.fecha}}</div>
          <div class="card-body">
            <h4 class="card-title">{{nota.titulo}}</h4>
            <p class="card-text">{{nota.texto}}</p>
            <button type="button" class="btn btn-danger" @click="eliminarNota(index)">Eliminar &times;</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data() {
      return {
        msg: 'App de Gestión de notas en Vue',
        nota: {
          titulo: '',
          texto: ''
        },
        notas: [{
          titulo: 'Terminar el curso',
          texto: 'Realizar curso de Vue 2',
          fecha: new Date(Date.now()).toLocaleString()
        }]
      }
    },
    methods: {
      agregarNota: function () {
        let { texto, titulo} = this.nota;
        this.notas.push({
          texto,
          titulo,
          fecha: new Date(Date.now()).toLocaleString()
        });
      },
      eliminarNota: function(index){
        this.notas.splice(index, 1);
      }
    }
  }

</script>

<style lang="scss">

</style>
