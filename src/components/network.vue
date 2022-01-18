
<template>
    <b-container>
          <div class="header2">
            <br>
            <h2 >Plots </h2>
          </div>

          <p>Ci sono due possibili ipotesi per spiegare la scomparsa dei 10 dipendenti della GAStech.</p>
          <p> La prima congettura è che i membri della POK abbiano effettivamente rapito i dipendenti  infiltrandosi durante la riunione della
            GAStech spacciandosi per ristoratori, per vendicare la morte della piccola Juliana Vann, oppure semplicemente per
            necessità di maggiori fondi.</p>
          <p>Un'altra possibile ipotesi riguarda la fuga del gruppo esucitivo della GAStech con parte dei profitti. Questa ipotesi viene
             supportata da alcune e-mail scambiate tra i dipendenti sui luoghi di vacanza e sull'innaffiamento delle piante per il mese successivo. </p>
<b-table-simple>
  <b-tr>
    <b-th>
        <b-form-group label="Membri rapiti">
          <b-form-radio-group
              v-model="kidnapped.value"
              :options="kidnapped.options"
              name="buttonsKidn"
              buttons
          ></b-form-radio-group>
        </b-form-group>
    </b-th>
    <b-th>
        <b-form-group label="Membership">
          <b-form-radio-group
              v-model="membership.value"
              :options="membership.options"
              name="buttonsMemb"
              button-variant="success"
              buttons
          ></b-form-radio-group>
        </b-form-group>
    </b-th>
  </b-tr>
</b-table-simple>
        <b-table-simple>
          <b-tr>
            <b-th>
                <bar_chart plotId="Age Rage" :aggregatedData="ageBindData" />
            </b-th>
            <b-th>
                <bar_chart plotId="Job type" :aggregatedData="jobTypeData" />
            </b-th>
            <b-th>
                <bar_chart plotId="Gender" :aggregatedData="gender" />
            </b-th>
          </b-tr>
        </b-table-simple>
        <div >
            <h2 class="header">Network</h2>
            <div >
                <network_graph
                    :networkNodesData="networkNodesData"
                    :networkLinksData="networkLinksData"/>
            </div>
        </div>

    </b-container>

</template>

<script>

import network_graph from "@/components/graph/network_graph.vue";
import bar_chart from "@/components/graph/bar_chart";
import crossfilter from "crossfilter2";

let cf;
let dimMembership;
let dimKidnapped;
let dimJobType;
let dimAgeBind;
let dimGender;


export default {
  name: "network",
  components: {
    network_graph,
    bar_chart,
  },
  data: function() {
    return {
      membership: {
        value: "",
        options: [],
      },
      kidnapped: {
        value: "",
        options: [],
      },
      ageBindData: [],
      jobTypeData: [],
      gender: [],

      networkNodesData: [],
      networkLinksData: [],
    };
  },

  mounted: function (){
    fetch("./static/data/persons2.json")
        .then(response => response.json())
        .then(data => {
          this.personsData = data.map(row => this.personsDataParsing(row));

          cf = crossfilter(this.personsData);

          dimMembership = cf.dimension(row => row.membership)
          dimKidnapped = cf.dimension(row => row.kidnapped);
          dimJobType = cf.dimension(row => row.jobType);
          dimAgeBind = cf.dimension(row => row.ageBind);
          dimGender = cf.dimension(row => row.gender)
          this.membership.options.push("All");
          this.membership.options.push(
              ...dimMembership
                  .group()
                  .reduceCount()
                  .all()
                  .map(row => row.key)
          );
          this.membership.value = "All";

          this.kidnapped.options.push("All");
          this.kidnapped.options.push(
              ...dimKidnapped
                  .group()
                  .reduceCount()
                  .all()
                  .map(row => row.key)
          );
          this.kidnapped.value = "All";
        });
  },
  watch: {
    membership: {
      handler(newVal) {
        if (newVal.value == "All") {
          dimMembership.filter(null);
        } else {
          dimMembership.filter(newVal.value);
        }
        this.refreshDashboard();
      },
      deep: true,
    },



    kidnapped: {
      handler(newVal) {
        if (newVal.value == "All") {
          dimKidnapped.filter(null);
        } else {
          dimKidnapped.filter(newVal.value);
        }
        this.refreshDashboard();
      },
      deep: true,
    },


  },
  methods: {
      personsDataParsing(row) {
      const parsedRow = {
        id: row.Id,
        name: row.FullName,
        gender: row.Gender,
        age: +row.Age,
        ageBind: row.AgeBind,
        jobType: row.CurrentEmploymentType,
        membership: row.Membership,
        kidnapped: row.Kidnapped,
        targetNodes: row.TargetNodes,

      };
      return parsedRow;
    },
    networkNodesDataParsing(row) {
      const parsedRow = {
        id: row.id,
        name: row.name,
      };
      return parsedRow;
    },
    networkLinksDataParsing(row) {
      let parsedRow = [];
      row.targetNodes.forEach(element => {
        parsedRow.push({ sid: row.id, tid: element });
      });
      return parsedRow;
    },
    refreshDashboard() {
      this.networkNodesData = cf
          .allFiltered()
          .map(row => this.networkNodesDataParsing(row));
      const filteredIds = new Set(cf.allFiltered().map(row => row.id));
      this.networkLinksData = cf
          .allFiltered()
          .flatMap(row => this.networkLinksDataParsing(row))
          .filter(d => filteredIds.has(d.tid));

      this.jobTypeData = dimJobType
          .group()
          .reduceCount()
          .all();
      this.ageBindData = dimAgeBind
          .group()
          .reduceCount()
          .all();
      this.gender = dimGender
          .group()
          .reduceCount()
          .all();

    },
  },
};

</script>{



<style scoped>

</style>