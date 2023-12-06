<template>
  <div class="w-screen h-screen p-5 bg-sky-100">
    <div class="flex flex-col gap-5">
      <div class="text-4xl">圖書管理系統</div>
      <addBook @add="add" />
      <showBook :bookData="bookData" @del="del" />
    </div>
  </div>
</template>

<script lang="ts" setup>
import addBook from "@/components/addBook.vue";
import showBook from "@/components/showBook.vue";
import { reactive } from "vue";

interface bookInfo {
  uid?: string;
  name: string;
  type: string;
  addtime: string;
}

interface bookList {
  [uid: string]: bookInfo;
}

const bookData = reactive<bookList>({});

const add = (book: bookInfo) => {
  const { uid, ...info } = book;
  bookData[uid] = info;
  ElMessage({
    message: "新增成功",
    grouping: true,
    type: "success",
  });
};

const del = (uid: string) => {
  ElMessageBox.confirm("你確定?確定?確?", "", {
    confirmButtonText: "狠心刪除",
    cancelButtonText: "算了",
    type: "warning",
  }).then(() => {
    delete bookData[uid];
    ElMessage({
      type: "success",
      grouping: true,
      message: "刪除成功.",
    });
  });
};
</script>

<style scoped></style>
