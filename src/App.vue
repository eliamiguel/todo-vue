<script setup>
  import { reactive } from 'vue';

  import Cabecalho from './Components/Cabecalho.vue';
  import Formulario from './Components/Formulario.vue';
  import ListaDetarefas from './Components/ListaDetarefas.vue';

const estado = reactive({
  filtro: 'todas',
  cadastrarTarefa:'',
  tarefas:[{
    titulo:'Estudar ES6',
    finalizada: false,
  },
{
  titulo: 'Estudar SASS',
  finalizada: false,
},
{
titulo: 'Ir para academia',
finalizada:true,
}]
})
const getTarefasPendentes = ()=>{
  return estado.tarefas.filter(tarefa => !tarefa.finalizada)
} 
const getTarefasFinalizadas = () =>{
  return estado.tarefas.filter(tarefa => tarefa.finalizada)
}
const tarefaFiltradas = () =>{
const filtro = estado.filtro;
switch (filtro) {
  case 'pendentes': 
    return getTarefasPendentes();
    case 'finalizadas': 
    return getTarefasFinalizadas ();
  default  : 
    return estado.tarefas;
}
}
const cadastrar = () =>{
  const tarefaNOva = {
    titulo:estado.cadastrarTarefa,
    finalizado: false
  }
  estado.tarefas.push(tarefaNOva);
  estado.cadastrarTarefa='';
}

</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes=" getTarefasPendentes().length " />;
    <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :cadastrar-tarefa="cadastrarTarefa" :edita-tarefa="evento => estado.cadastrarTarefa = evento.tarefa.value" :cadastrar=" cadastrar" />;
    <ListaDetarefas :tarefas="tarefaFiltradas()" />
</div>
  
</template>

