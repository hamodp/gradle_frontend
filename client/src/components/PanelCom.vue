<template>
  <div class="panel">
    <button type="button" @click="close">
       close
    </button>
    <component class="" :is="currentView" @close="close()" ></component>
  </div>
</template>

<script>
//import { jsPanel } from "../../node_modules/jspanel4/dist/jspanel.min.js";
import { jsPanel } from "jspanel4";
import table from "@/components/table.vue";

export default {
  name: "PanelCom",
  props: {
    msg: String,
    type: null
  },
  data: function() {
      
      var obj = this;
      var data = {
      component: null,
      panel: null,
      currentView : null,
      table: [{test:"test", attr:"attr"}]
      };

      return data;
  },
  mounted: function() {
      var obj = this;
      console.log("testing the mounted function");
      console.log(this.type);
      this.currentView = this.type;
      this.panel =  jsPanel.create({
    theme:       'primary',
    contentSize: {
        width: function() { return Math.min(730, window.innerWidth*0.9);},
        height: function() { return Math.min(400, window.innerHeight*0.5);}
    },
    position:    'center-top 0 250',
    animateIn:   'jsPanelFadeIn',
    headerTitle: 'I\'m a jsPanel',
    content: obj.$el,
    // content:     function (panel) {
    //     $(this.content).load('docs/sample-content/sampleContentHome.html', function () {
    //         $(panel.content).mCustomScrollbar({
    //             scrollButtons: {enable: true},
    //             theme: 'dark-thin'
    //         });
    //         Prism.highlightAll();
    //     });
    // },
    onwindowresize: true
});


  },
  methods: {
      close: function() {
          this.$emit("current-close");
          this.$emit("close");
          this.panel.close();
      },
      		currentClose(){
      console.log("emit heard");
			// this.currentView = null;
		}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "../../node_modules/jspanel4/dist/jspanel.min.css";
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.panel {
    background-color: white;
}
</style>

<!--template> 
  <div class="jspanel">
		<form>
			<p><input type="text" name="firstName"></p>
			<p><input type="text" name="lastName"></p>
		</form>
	</div>
</template>

<script>
import { jsPanel4 } from 'jspanel4'

export default
{
  name: PanelCom,
  mounted: function() {
     alert("jspanel4 loaded " + jsPanel4);
  }
};
</script>

<style scoped>
@import url("https://cdnjs.cloudflare.com/ajax/libs/jspanel3/3.9.3/jquery.jspanel.css");
</style-->