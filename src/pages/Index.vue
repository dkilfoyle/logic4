<template>
  <q-page class="column">
    <div class="row items-stretch" style="flex: 1">
      <div class="col-auto">
        <q-tabs v-model="leftTab" vertical switch-indicator class="leftBar">
          <q-tab name="mails" icon="mail" />
          <q-tab name="alarms" icon="alarm" />
          <q-tab name="movies" icon="movie" />
        </q-tabs>
      </div>
      <div class="col">
        <splitpanes style="height: 100%">
          <pane><div class="leftPanels">Left</div></pane>
          <pane>
            <splitpanes horizontal>
              <pane><div class="middlePanels"></div></pane>
              <pane><div class="middlePanels"></div></pane>
            </splitpanes>
          </pane>
          <pane><div class="rightPanels">Right</div></pane>
        </splitpanes>
      </div>
    </div>
    <div class="row statusBar"></div>
  </q-page>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { Splitpanes, Pane } from 'splitpanes';
import 'splitpanes/dist/splitpanes.css';

export default defineComponent({
  name: 'PageIndex',
  components: { Splitpanes, Pane },
  setup() {
    const leftTab = ref('mails');
    const rightTab = ref('movies');
    const leftSplitterModel = ref(30);
    const rightSplitterModel = ref(30);
    return { leftTab, rightTab, leftSplitterModel, rightSplitterModel };
  },
});
</script>

<style>
.leftBar {
  background: #f3f3f3;
  color: #65666e;
}

.leftPanels {
  background: #ebebeb;
  height: 100%;
}
.middlePanels {
  background: #fafafa;
  height: 100%;
}
.rightPanels {
  background: #fafafa;
  height: 100%;
}
.splitpanes {
  background-color: #f8f8f8;
}

.splitpanes__splitter {
  background-color: #ccc;
  position: relative;
}
.splitpanes__splitter:before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  transition: opacity 0.8s;
  background-color: #06a6e9;
  opacity: 0;
  z-index: 1;
}
.splitpanes__splitter:hover:before {
  opacity: 1;
}
.splitpanes--vertical > .splitpanes__splitter:before {
  left: -2px;
  right: -2px;
  height: 100%;
}
.splitpanes--horizontal > .splitpanes__splitter:before {
  top: -4x;
  bottom: -4px;
  width: 100%;
}
.q-tab__indicator {
  color: #00b1fb;
}

.q-tab--inactive {
  color: #bdbdc0;
}
.statusBar {
  background-color: #eeeeee;
  border-top: 1px solid #00b1fb;
  height: 30px;
}
</style>
