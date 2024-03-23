<script setup lang="ts">
import type { VNodeChild } from 'vue';
import { h, reactive } from 'vue';
import { NTag, type SelectOption } from 'naive-ui';

const formState = reactive({
  orgList: [
    { id: '1', name: '111', type: '10' },
    { id: '2', name: '222', type: '20' }
  ],
  orgId: null
});

const formState2 = reactive({
  orgList: [
    { value: '1', label: '111', type: '10' },
    { value: '2', label: '222', type: '20' }
  ],
  orgId: ''
});

function renderLabel(option: SelectOption): VNodeChild {
  return [
    h(NTag, { type: 'success', class: 'mr-2' }, { default: () => option.type }),
    (option.name ?? option.label) as string
  ];
}
</script>

<template>
  <div>
    {{ formState.orgId }}
    <NSelect
      v-model:value="formState.orgId"
      value-field="id"
      :options="formState.orgList"
      :render-label="renderLabel"
    />

    <hr />
    {{ formState2.orgId }}
    <NSelect v-model:value="formState2.orgId" :options="formState2.orgList" :render-label="renderLabel" />
  </div>
</template>

<style scoped></style>
