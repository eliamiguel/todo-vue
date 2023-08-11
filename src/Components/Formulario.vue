<script setup>
const props = defineProps(['cadastrar', 'cadastrarTarefa', 'TrocarFiltro', 'editaTarefa'])
</script>
<template>
  <form @submit.prevent="props.cadastrar">
    <div class="row">
      <div class="col">
        <input :value="props.cadastrarTarefa" @change="props.editaTarefa = props.editaTarefa " type="text" required placeholder="Digite aqui a descrição da tarefa" class="form-control">
      </div>
      <div class="col-md-2">
        <button class="btn btn-primary"  type="submit">Cadastrar</button>
      </div>
      <div class="col-md-2">
        <select @change="props.TrocarFiltro" class="form-control">
          <option value="todas">Todas tarefas</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>