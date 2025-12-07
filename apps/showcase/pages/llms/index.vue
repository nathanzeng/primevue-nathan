<template>
    <div class="card flex justify-content-center">
        <Toast />
        <Tree
            filter
            v-model:selectionKeys="selectedKey"
            :value="nodes"
            selectionMode="checkbox"
            class="w-full md:w-30rem"
        />
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { NodeService } from '../../assets/data/NodeService.js';
import { useToast } from 'primevue/usetoast';
import Tree from 'primevue/tree';

const nodes = ref(null);
const selectedKey = ref(null);
const toast = useToast();

onMounted(() => {
    NodeService.getTreeNodes().then((data) => (nodes.value = data));
});

const onNodeSelect = (node) => {
    toast.add({
        severity: 'success',
        summary: 'Node Selected',
        detail: node.label,
        life: 3000,
    });
};

const onNodeUnselect = (node) => {
    toast.add({
        severity: 'success',
        summary: 'Node Unselected',
        detail: node.label,
        life: 3000,
    });
};
</script>
