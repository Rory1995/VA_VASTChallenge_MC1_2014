<template>

  <div id="net">
    <b-table-simple>
      <b-tr>
        <b-th variant="dark">
          <div >
            <label >Dimensione nodi:    </label>
              <b-form-input id="range" v-model="nodeSize" type="range" min="1" max="40"></b-form-input>
            <div class="mt-2">Size: {{ nodeSize }}</div>
          </div>
        </b-th>
        <b-th variant="dark">
          <div >
            <label >Larghezza archi:    </label>
            <b-form-input id="range" v-model="linkWidth" type="range" min="1" max="15"></b-form-input>
            <div class="mt-2">Size: {{ linkWidth }}</div>
          </div>
        </b-th>
        <b-th variant="dark">
          <div >
            <label >Scegli la forza:    </label>
            <b-form-input id="range" v-model="force" type="range" min="300" max="3000"></b-form-input>
            <div class="mt-2">Forza: {{ force }}</div>
          </div>
        </b-th>
      </b-tr>

  </b-table-simple>
      <b-container style="background-color: #c4d4d0; border:1px solid #1c1b1b;">
        <d3-network
            :net-nodes="nodes"
            :net-links="links"
            :options="options"



        ></d3-network>
      </b-container>
    </div>

</template>

<script>
import D3Network from "vue-d3-network";

export default {
  components: {
    D3Network,
  },
  name: "network_graph",
  props: {
    networkNodesData: {required: true, type: Array},
    networkLinksData: {required: true, type: Array},
  },
  data() {
    return {
      status: 'Visibili',
      nodes: [],
      links: [],
      nodeSize:20,
      force: 500,
      nodeLabels: true,
      linkWidth: 1,
    };
  },
  computed: {
    options (){
      return{
        force: this.force,
        nodeSize: this.nodeSize,
        nodeLabels: Boolean(this.nodeLabels),
        linkWidth: this.linkWidth,

      }
    },
  },
    watch: {
      networkNodesData: function(newData) {
        this.nodes = newData;
      },
      networkLinksData: function(newData) {
        this.links = newData;
      },
    },
};
</script>



<style src="vue-d3-network/dist/vue-d3-network.css">


</style>