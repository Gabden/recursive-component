<template>
  <div>
    <ul class="directory-list">
      <node-tree :node="root" @expand="changeExpand"></node-tree>
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
  methods: {
    changeExpand(data) {
      this.$emit("expand", data);
    },
  },
};
</script>
