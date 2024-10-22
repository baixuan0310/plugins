<template>
  <Modal :title="'添加栏目'" width="600px">
    <template #footer>
      <el-button type="primary">保存</el-button>
    </template>
    <template #body>
      <el-form
        :model="currentEntity"
        ref="treeForm"
        label-width="100px"
        :rules="rules"
      >
        <el-form-item
          label="上级栏目"
          prop="parentId"
        >
          <el-select
            v-model="currentEntity.parentId"
            placeholder="请选择上级栏目"
          >
          </el-select>
        </el-form-item>
        <el-form-item
          label="栏目名称"
          prop="name"
        >
          <el-input
            v-model="currentEntity.name"
            placeholder="请输入栏目名称"
            clearable
          />
        </el-form-item>
        <el-form-item
          label="栏目别名"
          prop="alias"
        >
          <el-input
            v-model="currentEntity.alias"
            placeholder="请输入栏目别名"
            clearable
          />
        </el-form-item>
        <el-form-item
          label="栏目路径"
          prop="path"
        >
          <el-input
            v-model="currentEntity.path"
            placeholder="请输入栏目路径"
            clearable
          />
        </el-form-item>
        <el-form-item
          label="栏目描述"
          prop="description"
        >
          <el-input
            v-model="currentEntity.description"
            placeholder="请输入栏目描述"
            clearable
            type="textarea"
            :row="3"
          />
        </el-form-item>
      </el-form>
    </template>
  </Modal>
</template>

<script lang="ts" setup>
import { ref, inject, Ref } from "vue";
import { rules } from "../constant";
import Modal from "@/components/Modal";

const modalEntity: Ref = inject('modalEntity')!;

const currentEntity = ref(modalEntity.value.entity);

</script>

<style lang="scss" scoped>
</style>
