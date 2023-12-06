<template>
  <div class="w-full h-full p-1 bg-slate-50 rounded-lg border-2 border-sky-800">
    <el-table
      ref="tableRef"
      :data="Object.values(props.bookData)"
      style="width: 100%; height: 100%"
    >
      <el-table-column prop="name" label="書本名稱" />
      <el-table-column prop="type" label="語言類別" />
      <el-table-column prop="addtime" label="登錄時間" />
      <el-table-column fixed="right" label="刪除" width="120">
        <template #default="scope">
          <el-button
            type="danger"
            :icon="Delete"
            size="small"
            @click.prevent="delBook(scope.$index)"
            >Delete</el-button
          >
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script lang="ts" setup>
import { Delete } from "@element-plus/icons-vue";

interface bookInfo {
  name: string;
  type: string;
  addtime: string;
}

interface bookList {
  [uid: string]: bookInfo;
}

const props = defineProps<{
  bookData: bookList;
}>();

const emits = defineEmits<{
  (eventName: "del", uid: string): void;
}>();

const delBook = (index) => {
  const uid = Object.keys(props.bookData)[index];
  emits("del", uid);
};
</script>

<style scoped></style>
