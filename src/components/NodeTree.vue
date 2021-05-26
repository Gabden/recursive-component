<template>
  <li class="node" :class="isFolder ? 'folder' : 'file'">
    <div
      :class="isFolder ? 'dir-expand cursor' : null"
      @click="isExpanded = !isExpanded"
    >
      <p>
        {{ node.name }}
      </p>
    </div>

    <ul
      class="directory-list"
      v-if="isExpanded && node.children && node.children.length"
    >
      <node
        v-for="child in node.children"
        :node="child"
        :key="child.name"
      ></node>
    </ul>
  </li>
</template>

<script>
export default {
  name: "node",
  computed: {
    isFolder() {
      return this.node.type === "dir";
    },
  },
  props: {
    node: Object,
  },
  data() {
    return {
      isExpanded: false,
    };
  },
};
</script>
<style scoped>
.cursor {
  cursor: pointer;
}
</style>
