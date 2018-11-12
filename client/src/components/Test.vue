<template>
	<div class=test>
        This is a test app
    </div>
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
		  }
        }
</script>

<style scoped>
.test {
    background-color: black;
    color: white;
}
</style>