<template>
  <section class="flex items-center justify-between">
    <section>
      <el-popover
        trigger="click"
        width="230"
        placement="right"
        :hide-on-click="false"
      >
        <template #reference>
          <el-button class="btn" text>
            <svg
              width="20"
              height="20"
              viewBox="0 0 20 20"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M17.5 16.6667V5.00008C17.5 4.08091 16.7525 3.33341 15.8333 3.33341H14.1667V1.66675H12.5V3.33341H7.5V1.66675H5.83333V3.33341H4.16667C3.2475 3.33341 2.5 4.08091 2.5 5.00008V16.6667C2.5 17.5859 3.2475 18.3334 4.16667 18.3334H15.8333C16.7525 18.3334 17.5 17.5859 17.5 16.6667ZM7.5 15.0001H5.83333V13.3334H7.5V15.0001ZM7.5 11.6667H5.83333V10.0001H7.5V11.6667ZM10.8333 15.0001H9.16667V13.3334H10.8333V15.0001ZM10.8333 11.6667H9.16667V10.0001H10.8333V11.6667ZM14.1667 15.0001H12.5V13.3334H14.1667V15.0001ZM14.1667 11.6667H12.5V10.0001H14.1667V11.6667ZM15.8333 7.50008H4.16667V5.83342H15.8333V7.50008Z"
                fill="#546E7A"
              />
            </svg>
          </el-button>
        </template>
        <section class="financial-page-menu">
          <section class="grid grid-cols-1 gap-4">
            <el-date-picker v-model="date.from" />
            <el-date-picker v-model="date.to" />
            <el-button class="btn btn-primary rounded-lg">Filter</el-button>
          </section>
        </section>
      </el-popover>
    </section>
    <section class="w-24">
      <el-select
        v-model="activeType"
        class="border border-gray-300 rounded-lg"
        @change="emit('activeType', activeType)"
      >
        <el-option
          v-for="type in reportTypes"
          :key="type"
          :label="type"
          :value="type"
        />
      </el-select>
    </section>
  </section>
</template>

<script setup>
const reportTypes = ref(["All", "Views", "Likes"]);
const activeType = ref("All");
const date = reactive({
  from: "",
  to: "",
});
const emit = defineEmits("activeType");
</script>

<style scoped></style>
