<template>
  <li :class="isFolder ? 'node folder' : 'file'">
    <div :class="isFolder ? 'cursor dir-expand' : null" @click="changeExpand">
      <p>
        {{ node.name }}
      </p>
    </div>

    <ul
      class="directory-list"
      v-if="node.isExpanded && node.children && node.children.length"
    >
      <node
        v-for="child in node.children"
        :node="child"
        :key="child.name"
        @expand="changeExpandChild"
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
  methods: {
    changeExpand() {
      this.$emit("expand", {
        name: this.node.name,
        isExpanded: !this.node.isExpanded,
      });
    },
    changeExpandChild(data) {
      this.$emit("expand", data);
    },
  },
};
</script>
<style scoped>
.cursor {
  cursor: pointer;
}
</style>
