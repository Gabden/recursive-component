<template>
  <div>
    <ul class="directory-list">
      <node-tree :node="root"></node-tree>
    </ul>
  </div>
</template>

<script>
import NodeTree from "@/components/NodeTree.vue";
export default {
  components: {
    NodeTree,
  },
  props: {
    root: {
      type: Object,
      required: true,
    },
  },
};
</script>
