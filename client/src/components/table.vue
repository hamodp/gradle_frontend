<template>
		<table class="table table-bordered">
		   <tr>
    	       <th v-for="(col, header) in title[0]" :key=col v-on:click="sort"
    	       v-on:dragstart="drag" v-on:dragover="allowDrop" v-on:drop="drop"
    	        draggable="true">{{ header }}</th>
    	   </tr>
    	   <tr v-for="row in title" :key="row">
    	      <td v-for="col in row" :key="col">{{ col }}</td>
    	   </tr>
		  </table>
		  
</template>

<script>
    export default {
		  props: ['title'],
		  data: function(){
			  var data= {
					  sorter: '',
					  dragTarget: ''
              };
              
              return data;
		  },
		  methods:{
			sort: function(event){
				var sortKey = event.target.innerText
				
				if(sortKey == this.sorter){
					this.title.reverse();
				}
				else{
					this.title.sort(function(a, b){
						return (a[sortKey] < b[sortKey]) - (a[sortKey]> b[sortKey]);
					});
					this.sorter = sortKey;
				}
			},
			allowDrop: function(ev) {
			    ev.preventDefault();
			},

			drag: function(ev) {
			    ev.dataTransfer.setData("text", ev.target.innerText);
			    this.dragTarget = ev.target.innerText;
			    
			},

			drop: function(ev) {
			    ev.preventDefault();
			    console.log(ev);
			    var data = ev.dataTransfer.getData("text");
			    this.insertCol(data, ev.target.innerText);
			},
			insertCol(move, target){
				for(var i=0; i<this.title.length; i++){
					var obj ={};
					var row = this.title[i];
					for(col in row){
						if(col == target){
							obj[move] = row[move];
							obj[col] = row[col];
						}
						else if(col != move){
							obj[col] = row[col];
						}
					}
					
					Vue.set(this.title, i, obj);
				}
			}
		  },

        }
</script>