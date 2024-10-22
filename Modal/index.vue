<template>
  <div class="app-container">
    <TreeEditor v-if="treeModal.visible" />
  </div>
</template>

<script setup>
import { provide } from "vue";

class EditorModalEntity {
  constructor(visible, type, entity) {
    this.visible = visible || false;
    this.type = type || "add";
    this.entity = entity || {};
  }
  openAdd(entity) {
    this.visible = true;
    this.type = "add";
    this.entity = deepClone(entity);
  }
  openEdit(entity) {
    this.visible = true;
    this.type = "edit";
    this.entity = deepClone(entity);
  }
  close() {
    this.visible = false;
  }
}

const treeModal = ref(new EditorModalEntity());
provide("modalEntity", treeModal);

const TreeEditor = defineAsyncComponent(() =>
  import("./components/treeEditor.vue")
);
</script>

<style lang="scss" scoped></style>
