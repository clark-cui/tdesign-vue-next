<template>
  <div class="tdesign-tree-base">
    <div class="operations">
      <t-form label-width="120">
        <t-form-item label="互斥展开">
          <t-switch v-model="mutex" />
        </t-form-item>
        <t-form-item label="整个节点可点击">
          <t-switch v-model="expandOnClickNode" />
        </t-form-item>
      </t-form>
    </div>
    <t-tree
      :data="items"
      hover
      :expand-mutex="mutex"
      :expand-on-click-node="expandOnClickNode"
      @click="onClick"
      @expand="handleExpand"
    />
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue';

const items = [
  {
    label: '1',
    children: [
      {
        label: '1.1',
        children: [
          {
            label: '1.1.1',
          },
          {
            label: '1.1.2',
          },
        ],
      },
      {
        label: '1.2',
        children: [
          {
            label: '1.2.1',
          },
          {
            label: '1.2.2',
          },
        ],
      },
    ],
  },
  {
    label: '2',
    children: [
      {
        label: '2.1',
        children: [
          {
            label: '2.1.1',
          },
          {
            label: '2.1.2',
          },
        ],
      },
      {
        label: '2.2',
        children: [
          {
            label: '2.2.1',
          },
          {
            label: '2.2.2',
          },
        ],
      },
    ],
  },
];

export default defineComponent({
  setup() {
    const mutex = ref(true);
    const expandOnClickNode = ref(true);

    const onClick = (context) => {
      console.info('onClick', context);
    };

    const handleExpand = (value, context) => {
      console.info('onExpand', value, context);
    };

    return {
      mutex,
      expandOnClickNode,
      items,
      onClick,
      handleExpand,
    };
  },
});
</script>
<style scoped>
.tdesign-tree-base .t-button {
  margin: 0 10px 10px 0;
}

.operations {
  margin-bottom: 32px;
}
</style>
