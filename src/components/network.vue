<template>
<div id="network">

</div>
</template>

<script>


//const d3 = require('d3');


export default {
  name: "network",

  data: function() {
    return {
      dataPersons: [],
      networkNodesData: [],
      networkLinksData: [],
    };
  },

  mounted(){
    fetch("/static/data/persons2.json")
        .then(response => response.json())
        .then(data => {
          this.dataPersons = data.map(row => {
          const editedRow = {
            id: row.Id,
            name: row.FullName,
            gender: row.Gender,
            age: +row.Age,
            membership: row.Membership,
            cssClass: row.CssClass,
            labelClass: row.LabelClass,
            targetNodes: row.TargetNodes,
          };
            return editedRow;
        });

        });
},
}

</script>{



<style scoped>

</style>