<template>
  <el-dialog v-model="currentVisible" :title="title" :width="width || '800px'" destroy-on-close @closed="closeCurrentModal"
    align-center>
      <template #footer>
        <slot name="footer"></slot>
        <el-button @click="closeCurrentModal">关闭</el-button>
      </template>
      <div class="dialog-body-custom">
        <slot name="body"></slot>
      </div>
    </el-dialog>
</template>

<script lang='ts' setup>
import { defineProps, defineEmits, ref, defineAsyncComponent, inject, Ref } from "vue";
import { onMounted } from "vue";

// props&inject
const props = defineProps<{
  title: string;
  width?: string;
}>();
const modalEntity: Ref = inject('modalEntity')!;

// modal
const currentVisible = ref(false);
const closeCurrentModal = () => {
  currentVisible.value = false;
  setTimeout(() => {
    modalEntity.value.close();
  }, 300);
};

onMounted(async () => {
  currentVisible.value = modalEntity.value.visible;
});
</script>

<style lang='scss' scoped>
.dialog-body-custom{
  padding: 24px;
}
</style>