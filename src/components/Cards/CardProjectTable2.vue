<template>
  <!-- Projects Table Column -->
  <a-card :bordered="false" class="header-solid h-full" :bodyStyle="{ padding: 0 }">
    <template #title>
      <a-row type="flex" align="middle">
        <a-col :span="24" :md="12">
          <h5 class="font-semibold m-0">Projects Table</h5>
        </a-col>
        <a-col
          :span="24"
          :md="12"
          style="display: flex; align-items: center; justify-content: flex-end"
        >
          <a-radio-group v-model="projectHeaderBtns" size="small">
            <a-radio-button value="all">ALL</a-radio-button>
            <a-radio-button value="online">ONLINE</a-radio-button>
            <a-radio-button value="stores">STORES</a-radio-button>
          </a-radio-group>
        </a-col>
      </a-row>
    </template>
    <a-table :customRow="rowClick" :columns="columns" :data-source="data" :pagination="false">
      <template #expandedRowRender="{ record }">
        <p style="margin: 0">{{ record.company.name }}</p>
      </template>
      <template #name="{ text }">
        <a>{{ text }}</a>
      </template>

      <a-space slot="members" slot-scope="members" :size="-12" class="avatar-chips">
        <template #members="{ text: members }">
          <a-avatar v-for="member in members" :key="member" size="small" :src="member" />
        </template>
      </a-space>

      <template #company="{ text: company }">
        <h6 class="m-0">
          <img :src="company.logo" width="25" style="margin-right: 10px" />
          {{ company.name }}
        </h6>
      </template>

      <template #editExec="{ text: row }">
        <a @click.stop="execClick(row)">
          <RightCircleTwoTone :style="{ fontSize: '24px' }" />
        </a>
      </template> -->
    </a-table>
  </a-card>
  <!-- / Projects Table Column -->
</template>

<script setup lang="ts">

import { RightCircleTwoTone } from '@ant-design/icons-vue';

defineProps({
  data: {
    type: Array,
    default: () => [],
  },
  columns: {
    type: Array,
    default: () => [],
  },
});

const rowClick = (record: any) => {
  return {
    onClick: (event: any) => {
      console.log("Click Row")
    },
  }
}

const execClick = (record: any) => {
  console.log("Click Button", record)
}

// Active button for the "Projects" table's card header radio button group.
let projectHeaderBtns = "all";
</script>