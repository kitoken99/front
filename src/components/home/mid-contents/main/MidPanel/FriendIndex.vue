<template>
  <div style="display: flex; flex-direction: column; height: 100%">
    <div style="flex: 1">
      <q-tab-panels
        v-model="tab"
        animated
        style="height: 100%"
        v-show="store.getters['state/getIsShowRoom']"
      >
        <q-tab-panel name="profile">
          <FriendPanel class="panel" />
        </q-tab-panel>
        <q-tab-panel name="friends">
          <FriendPanel class="panel" />
        </q-tab-panel>
        <q-tab-panel name="talks">
          <TalkPanel class="panel" />
        </q-tab-panel>
      </q-tab-panels>
    </div>
    <q-separator />
    <div>
      <q-tabs
        v-show="store.getters['state/getIsShowRoom']"
        v-model="tab"
        :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
        align="justify"
        narrow-indicator
        switch-indicator
        style="height: 56px"
      >
        <q-tab name="profile" label="profile" />
        <q-tab name="friends" label="friends" />
        <q-tab name="talks" label="talks" />
      </q-tabs>
    </div>
  </div>
</template>
<script>
import { defineComponent, ref } from "vue";
import { useStore } from "vuex";
import FriendPanel from "./panels/FriendPanel.vue";
import TalkPanel from "./panels/TalkPanel.vue";
export default defineComponent({
  name: "FriendIndex",
  components: {
    FriendPanel,
    TalkPanel,
  },
  setup() {
    const store = useStore();
    const tab = ref("friends");
    return {
      store,
      tab,
    };
  },
});
</script>
<style>
.panel {
  height: 100%;
}
</style>
