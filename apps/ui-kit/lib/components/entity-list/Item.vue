<template>
  <stateless-sidebar-folder
    v-if="source.type === 'schema'"
    v-show="!source.hidden"
    :expanded="source.expanded"
    :schema="source.entity"
    @expand="onExpand($event, source)"
    @contextmenu.prevent.stop="onContextMenu($event, source)"
  />
  <stateless-table-list-item
    v-else-if="source.type === 'table'"
    :level="source.level"
    :expanded="source.expanded"
    :table="source.entity"
    :pinned="source.pinned"
    :loading-columns="source.loadingColumns"
    :enable-pinning="enablePinning"
    @dblclick="onDblClick($event, source)"
    @expand="onExpand($event, source)"
    @pin="onPin($event, source)"
    @contextmenu.prevent.stop="onContextMenu($event, source)"
  />
  <stateless-routine-list-item
    v-else-if="source.type === 'routine'"
    :level="source.level"
    :expanded="source.expanded"
    :routine="source.entity"
    :pinned="source.pinned"
    :enable-pinning="enablePinning"
    @expand="onExpand($event, source)"
    @pin="onPin($event, source)"
    @contextmenu.prevent.stop="onContextMenu($event, source)"
  />
</template>

<script lang="ts">
import Vue from "vue";
import StatelessTableListItem from "./StatelessTableListItem.vue";
import StatelessRoutineListItem from "./StatelessRoutineListItem.vue";
import StatelessSidebarFolder from "./StatelessSidebarFolder.vue";
export default Vue.extend({
  components: {
    StatelessTableListItem,
    StatelessRoutineListItem,
    StatelessSidebarFolder,
  },
  props: ["source", "onExpand", "onPin", "onDblClick", "onContextMenu", "enablePinning"],
});
</script>
