<template>
<div id="jspanel_test">
  <h1>JsPanel + VueJS</h1>
  <!--component :is="currentView" @current-close="currentClose"></component-->
  <component v-for="app in apps" :key="app.name" :is="app" @close="close(app)" :type="currentView"></component>
  <button type="button" @click="jsPanelClick">
    JsPanel
  </button>
    <button type="button" @click="jsPanelClick2">
    JsPanel
  </button>
	Show : {{currentView}}
</div>
</template>

<script src="https://unpkg.com/vue"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jspanel3/3.9.3/jquery.jspanel-compiled.js"></script>
<script>
import PanelCom from "@/components/PanelCom.vue";
import HelloWorld from "@/components/HelloWorld.vue";
import Test from "@/components/Test.vue"

export default {
  name: "about",
  components: null,
  data: function() {
    var data = {
    currentView: null,
    apps: []
    };
    
    return data;
  },
  methods: {
    jsPanelClick() {
      console.log(this.apps);
      this.apps.push(PanelCom);
      this.currentView = HelloWorld;
      console.log(PanelCom);
    },
     jsPanelClick1() {
       this.components = {
         HelloWorld
       };
       this.currentView = HelloWorld;
       console.log(HelloWorld);
    },
    jsPanelClick2() {
       this.components = {
         Test
       };
       this.apps.push(PanelCom);
       this.currentView = PanelCom;
       this.currentView = Test;
       console.log(Test);
    },

		currentClose(){
      console.log("emit heard");
      this.currentView = null;
      console.log(this.apps);
    },
    close(app) {
      console.log(app);
      this.apps.pop();
      console.log(this.apps);

    }
  }
};
</script>
