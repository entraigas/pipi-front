<script setup lang="ts">
import type { IAlumno, IDocente, IMateria } from '~/assets/interfaces/index'
import { listDocentes } from '~/assets/services/docente'
import { listAlumnos } from '~/assets/services/alumno'
import { listMaterias } from '~/assets/services/materia'

const docentes = ref<IDocente[]>([])
const alumnos = ref<IAlumno[]>([])
const materias = ref<IMateria[]>([])

onMounted(async () => {
  docentes.value = await listDocentes()
  alumnos.value = await listAlumnos()
  materias.value = await listMaterias()
})
</script>

<template>
  <div>
    <h1>listado de profesores</h1>
    <ul>
      <li v-for="(item, index) in docentes" :key="index">
        {{ item.nombre }}
      </li>
    </ul>

    <h1>listado de alumnos</h1>
    <ul>
      <li v-for="(item, index) in alumnos" :key="index">
        {{ item.nombre }}
      </li>
    </ul>

    <h1>listado de materias</h1>
    <ul>
      <li v-for="(item, index) in materias" :key="index">
        {{ item.nombre }}
      </li>
    </ul>
  </div>
</template>
