<template>
    <Multiselect v-model="columns" :options="fields" />
    <Datatable :value="data" show-gridlines resizable-columns column-resize-mode="expand">
        <Column v-for="col in columns" :header="col" :field="col"> </Column>
    </Datatable>
</template>

<script setup>
import { ref } from 'vue';

const data = [
    { a: 'a1', b: 'b1', c: 'c1', d: 'd1' },
    { a: 'a2', b: 'b2', c: 'c2', d: 'd2' },
    { a: 'a3', b: 'b3', c: 'c3', d: 'd3' }
];

const fields = ['a', 'b', 'c', 'd'];
const columns = ref(fields);
</script>
