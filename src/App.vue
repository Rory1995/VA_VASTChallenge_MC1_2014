<template>
  <b-table-simple>
    <div id="app">

      <nav class="navbar navbar-expand-sm bg-dark navbar-dark fixed-top" >
        <a class="navbar-brand"  href="#"><img src="./assets/logo.png" class="d-inline-block align-top" alt="logo">
          VAST Challenge 2014
        </a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item active">
              <a class="nav-link" href="#">Mini Challenge 1 <span class="sr-only">(current)</span></a>
            </li>
          </ul>
        </div>
      </nav>

      <b-tr>
        <timeline> </timeline>
      </b-tr>
      <b-tr>
        <network> </network>
      </b-tr>
      <b-tr >
        <organization_chart> </organization_chart>
      </b-tr>




     </div>
  </b-table-simple>
</template>
<script type="text/javascript">
import timeline from "@/components/timeline.vue";
import organization_chart from "@/components/organization_chart.vue";
import network from "@/components/network.vue";


export default {
  name: 'App',
  components: {timeline,
               organization_chart,
               network},
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}



</style>
