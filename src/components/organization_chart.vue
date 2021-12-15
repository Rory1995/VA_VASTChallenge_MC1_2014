<template>
  <div class="container">
    <div class="header">
      <br>
      <h1 >Protectors of Kronos </h1>
    </div>
    <h3>POK organization chart </h3>
    <b-form-group variant="outline-success" label="Osserva come è cambiato l'roganizzazione della POK selezionando l'anno ed esplorando l'organigramma" v-slot="{ ariaDescribedby }">
      <b-form-radio-group
          id="btn-radios-1"
          v-model="selected"
          :options="options"
          :aria-describedby="ariaDescribedby"
          name="radios-btn-default"
          buttons
      ></b-form-radio-group>
    </b-form-group>
    <br>

    <b-row>
      <b-col>
        <vue-tree
        style=" height: 480%; border: 1px solid rgba(39,39,128,0); background: rgba(57,60,66,0.88)"
        :dataset="organization2009"
        :config="treeConfig"
        :linkStyle="'straight'"
    >

      <template v-slot:node="{ node, collapsed }">

        <div
            class="rich-media-node"
            :style="{ border: collapsed ? '2px solid grey' : '' }"
        >
          <img
              :src="node.avatar"
              style="width: 30px; height: 30px; border-raduis: 10px;"
          />
          <span style="padding: 3px 0; font-weight: bold;"
          ><i>{{ node.name }}</i>
          {{ node.value }}</span>
        </div>
      </template>
    </vue-tree>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import VueTree from "@ssthouse/vue-tree-chart";
import Vue from "vue";
Vue.component("vue-tree", VueTree);

export default {
  name: "organization_chart",
  data() {
    return {

      selected: '1997',
      options: [
        { text: '1997', value: 'radio1' },
        { text: '2001', value: 'radio2' },
        { text: '2009', value: 'radio4' }
      ],
      organization1997: {
        name: 'Henk Bodrogi,',
        value: 'Leader',
        avatar: "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
        children: [{
      name: "Fondatori",
      avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
            children: [
              {
                name: "Carmine Osvaldo,",
                value: 'Fondatore',
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
              },
              {
                name: "Ale L. Hanne,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",

              },
              {
                name: "Jeroen Karel,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
              },
              {
                name: "Valentine Mies,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
              },
              {
                name: "Joreto Katell,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
              },
              {
                name: "Yanick Cato,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
              }
          ]
        },
        ]
      },
      organization2001: {
        name: 'Elian Karel,',
        value: 'Leader',
        avatar:"https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
        children: [
          {
            name: "Lucio Jakab,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
          },
          {
            name: "Lorenzo Di Stefano,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
          },
          {
            name: "Mandor Vann,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
            children: [{
              name: "Isia Vann,",
              value: 'Membro, GAStech',
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",

            }]
          },
          {
            name: "Silvia Marek,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
          },
          {name: "Fondatori",
          value: "",
          avatar:
              "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
          children: [
            {
              name: "Carmine Osvaldo,",
              value: 'Fondatore',
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
            },
            {
              name: "Ale L. Hanne,",
              value: "Fondatore",
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",

            },
            {
              name: "Jeroen Karel,",
              value: "Fondatore",
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
            },
            {
              name: "Valentine Mies,",
              value: "Fondatore",
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
            },
            {
              name: "Joreto Katell,",
              value: "Fondatore",
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
            },
            {
              name: "Yanick Cato,",
              value: "Fondatore",
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
            }
          ]
        },
        ]
      },
      organization2009: {
        name: 'Silvia Marek,',
        value: 'Leader',
        avatar:"https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
        children: [
          {
            name: "Lucio Jakab,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
          },
          {
            name: "Lorenzo Di Stefano,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
          },
          {
            name: "Mandor Vann,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
            children: [{
              name: "Isia Vann,",
              value: 'Membro, GAStech',
              avatar:
                  "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",

            },
              {
                name: "Edvar Vann,",
                value: 'Membro, GAStech',
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",

              }]
          },
          {
            name: "Silvia Marek,",
            value: 'Membro',
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
          },
          {name: "Fondatori",
            value: "",
            avatar:
                "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
            children: [
              {
                name: "Carmine Osvaldo,",
                value: 'Fondatore',
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
                children:[{
                  name: "Hennie Osvaldo,",
                  value: "Membro, GAStech",
                  avatar:
                      "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
                }]
              },
              {
                name: "Ale L. Hanne,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",

              },
              {
                name: "Jeroen Karel,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
              },
              {
                name: "Valentine Mies,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
                children:[{
                  name: "Minke Mies,",
                  value: "Membro, GAStech",
                  avatar:
                      "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png",
                }]
              },
              {
                name: "Joreto Katell,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
              },
              {
                name: "Yanick Cato,",
                value: "Fondatore",
                avatar:
                    "https://www.corsinvest.it/wp-content/uploads/2019/10/github-logo.png"
              }
            ]
          },
        ]
      },
      treeConfig: { nodeWidth: 120, nodeHeight: 80, levelHeight: 170 }
    };
  }
};
</script>

<style scoped>

div.header{
  text-align: center;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: revert;
}

.box {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 200px;
}
.box>*:first-child {
  align-self: stretch;
}
.box .selected {
  align-self: center;
}

.rich-media-node {
  width: 110px;
  padding: 8px;
  display: flex;
  flex-direction: row;
  align-items: self-start ;
  justify-content: center;
  color: #313131;
  background-color: #5dc275;
  border-radius: 4px;

}
</style>