<template>
  <div class="grid grid-cols-12 gap-2 justify-items-center items-center">
    <p>書本名稱</p>
    <div class="col-span-2 w-full">
      <el-input
        v-model="bookName"
        placeholder=""
        style="height: 100%; width: 100%"
      />
    </div>

    <p>語言類別</p>
    <div class="col-span-2 w-full">
      <el-select
        v-model="bookTypeSelect"
        placeholder=""
        style="height: 100%; width: 100%"
      >
        <el-option
          v-for="item in bookType"
          :key="item"
          :label="item"
          :value="item"
        />
      </el-select>
    </div>

    <el-button
      type="success"
      :icon="Plus"
      style="height: 100%; width: 50%"
      @click="addAction"
    ></el-button>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import { Plus } from "@element-plus/icons-vue";
import { v4 as uuidv4 } from "uuid";
const bookName = ref("");
const bookTypeSelect = ref("");
const bookType = ["中文", "英文", "日文"];

interface bookInfo {
  uid: string;
  name: string;
  type: string;
  addtime: string;
}

const emits = defineEmits<{
  (eventName: "add", info: bookInfo): void;
}>();

const datetimeStr = (): string => {
  const date = new Date();
  const Y = date.getFullYear();
  const M =
    "-" +
    (date.getMonth() + 1 <= 10
      ? "0" + (date.getMonth() + 1)
      : date.getMonth() + 1);
  const D = "-" + (date.getDate() < 10 ? "0" + date.getDate() : date.getDate());
  const h =
    " " + (date.getHours() < 10 ? "0" + date.getHours() : date.getHours());
  const m =
    ":" +
    (date.getMinutes() < 10 ? "0" + date.getMinutes() : date.getMinutes());
  const s =
    ":" +
    (date.getSeconds() < 10 ? "0" + date.getSeconds() : date.getSeconds());
  return Y + M + D + h + m + s;
};

const addAction = () => {
  if (bookName.value === "" || bookTypeSelect.value === "") {
    ElMessage({
      message: "書本名稱和語言類別不可為空",
      grouping: true,
      type: "error",
    });
    return;
  }

  let bookInfo = {
    uid: uuidv4(),
    name: bookName.value,
    type: bookTypeSelect.value,
    addtime: datetimeStr(),
  };
  
  emits("add", bookInfo);
};
</script>

<style scoped></style>
