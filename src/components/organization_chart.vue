<template>

  <b-container>

  <div>

    <div class="header">
      <b-row>
        <b-col>
          <br>
          <h1 >Protectors of Kronos </h1>
        </b-col>
        <b-col>
         <img src="../../public/static/j_vann.jpg" >
        </b-col>
      </b-row>
    </div>

      <b-row>
          <p>Come abbiamo visto, una delle possibili spiegazioni della scomparsa dei dipendenti della GAStech
            è il rapimento da parte della POK. Ma come si è formato questo gruppo? Com'è acambiato negli anni? </p>
          <p>Il gruppo è stato formato nel 1997 a Elodis, perché negli ultimi 18 mesi era stato notato un incremento di malattie come cancro,
            malattie neurologiche, difetti di nascita e malattie respiratorie, associate ad calo della produzione agricola.
            La fonte specifica della contaminazione non era chiara, ma diverse persone credevano che fosse il risultato
            delle operazioni di trivellazione del gas a diversi chilometri da parte della GAStech.</p>


      </b-row>
          <p>Quando divenne chiaro che il Consiglio non poteva concordare una linea d'azione, i cittadini decisero
            di affrontare il problema in modo indipendente. Volevano portare il loro messaggio al governo e al resto dei cittadini,
            per riuscire a portare portare acqua pulita a Elodis e ripulire la contaminazione del fiume.</p>
          <p>Il momento più critico è quando, il 18 agosto 1998, Juliana Vann, dieci anni, muore di
            leucemia associata alla tossicità del benzene. Nipote di Mandor Vann e sorella di Isia Vann dipendente GAStech e membro attivo della POk.
          </p>




    <h3>POK organization chart </h3>
    <b-form-group variant="outline-success" label="Osserva come è cambiata l'organizzazione della POK selezionando l'anno di interesse ed esplorando l'organigramma" v-slot="{ ariaDescribedby }">
      <h5>POK {{selected}}</h5>
      <b-form-radio-group
          id="btn-radios-1"
          v-model="selected"
          :options="options"
          :aria-describedby="ariaDescribedby"
          name="year_button"
          buttons
      ></b-form-radio-group>
    </b-form-group>
    <br>

    <b-row>
      <b-col>
        <div class="org" style="height: 500%">

        <vue-tree
        style=" height: 480%; border: 1px solid rgba(0,0,0,0); background: rgb(241,245,243)"
        :dataset=organization[selected]
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
              style="width: 30px; height: 30px;"
          />
          <span style="padding: 3px 0; font-weight: bold;"
          ><i>{{ node.name }}</i>
          {{ node.value }}</span>
        </div>
      </template>
    </vue-tree>
        </div>
      </b-col>
    </b-row>

  </div>
  </b-container>
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
        { text: '1997', value: '1997' },
        { text: '2001', value: '2001' },
        { text: '2009', value: '2009' }
      ],
      organization:{
      "1997": {
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
      "2001": {
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
      "2009": {
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
      },
      treeConfig: { nodeWidth: 120, nodeHeight: 80, levelHeight: 170 }
    };
  },

};

</script>

<style scoped>

img {
  width: 100px;
}

div.header{
  text-align: center;
}

.org {
  display: flex ;
  flex-direction: column;
  align-items: revert;
}

.box>*:first-child {
  align-self: stretch;
}

.rich-media-node {
  width: 110px;
  padding: 8px;
  display: flex;
  flex-direction: row;
  align-items: self-start ;
  justify-content: center;
  color: #ffffff;
  background-color: #5dc275;
  border-radius: 4px;

}
</style>