<template>

    <div id="timeline">
      <div class="timeline">
        <br>
        <row>
          <h1>Eventi dei giorni 20 e 21 Gennaio 2014</h1>
        </row>
        <b-container>
        <div class="text">
          <span>Durante la riunione annuale della GAStech tenuta nella giornata del 20 gennaio 2014 è scattato un allerme e le persone che erano all'interno dell'edificio sono state essere evuacuate. Al termine dell'emergenza alcuni dipendenti non sono ricomparsi. Potete esplorare gli eventi di quel giorno grazie alla timeline sottostante. E' possibile leggere maggiori dettagli passando con il cursore sopra i diversi eventi.</span>
        </div>
        </b-container>
      </div>
    </div>

</template>

<script>
import {DataSet} from "vis-data/peer";
import {Timeline} from "vis-timeline/peer";
import "vis-timeline/styles/vis-timeline-graph2d.css";

export default {
  name: "timeline",

  mounted() {
    // DOM element where the Timeline will be attached
    const container = document.getElementById("timeline");

    // Create a DataSet (allows two way data-binding)
    const items = new DataSet([
      {
        id: 1,
        content: "Riunione annuale di GAStech",
        start: new Date(2014, 1, 20, 8),
        end: new Date(2014, 1, 20, 10),
        type: "background"
      },
      {id: 2, content: "Scatta allarme antincendio", start: new Date(2014, 1, 20, 10, 18)},
      {
        id: 3,
        content: "Evacuazione",
        title: "I dipendenti GAStech vengono evacuati dall'edificio e un elicottero parte dal tetto",
        start: new Date(2014, 1, 20, 10, 20,)
      },
      {
        id: 4,
        content: "Sospetto allarme bomba",
        title: "Si ipotizza che questa evacuazione sia causata da un allarme bomba",
        start: new Date(2014, 1, 20, 10, 27,)
      },
      {
        id: 5,
        content: "Arrivo pompieri",
        title: "Arrivo pompieri e perlustrazione edificio",
        start: new Date(2014, 1, 20, 10, 25),
        type: 'point'
      },
      {
        id: 6,
        content: "I dipendenti della GAStech iniziano a rientrare",
        start: new Date(2014, 1, 20, 10, 45),
        type: 'point'
      },
      {
        id: 7,
        content: "Membri scomparsi",
        title: "Il CEO e il gruppo esecutivo non sono riapparsi",
        start: new Date(2014, 1, 20, 11)
      },
      {id: 8, content: "Arrivo della polizia", start: new Date(2014, 1, 20, 12, 20), type: 'point'},
      {
        id: 9,
        content: "Arrivo CEO",
        title: "Solo il CEO arriva al ricevimento previsto nella capitale, parte un jet privato",
        start: new Date(2014, 1, 20, 12, 30)
      },
      {
        id: 10,
        content: "Ipotesi fuga",
        title: "Si ipotizza una fuga dei dirigente con il denaro delle casse di Kronos",
        start: new Date(2014, 1, 20, 12, 32)
      },
      {
        id: 11,
        content: "Comunicazione scomparsa",
        title: "I media comunicano la scomparsa di alcuni dipendenti di GAStech",
        start: new Date(2014, 1, 20, 13, 56)
      },
      {
        id: 12,
        content: "Arrivo funzionari governo",
        title: "I funzionari del governo Kronos sono arrivati a GAStech",
        start: new Date(2014, 1, 20, 14),
        type: 'point'
      },
      {
        id: 13,
        title: "I dipendenti della GAStech sono stati autorizzati a lasciare l'edificio",
        start: new Date(2014, 1, 20, 15, 20),
        type: 'point'
      },
      {
        id: 14,
        content: "Avvistate persone in nero",
        title: "Un dipendente della GAStech riferisce di aver visto diverse persone vestite di nero",
        start: new Date(2014, 1, 20, 15, 40)
      },
      {
        id: 15,
        content: "Interrogatori, focus su E.Vann",
        start: new Date(2014, 1, 20, 15),
        end: new Date(2014, 1, 20, 17),
        type: "background"
      },
      {
        id: 16,
        content: "Si scopre che le persone in nero presenti quella mattina erano i ristoratori",
        start: new Date(2014, 1, 20, 17)
      },
      {
        id: 17,
        content: "Ipotesi rapimento",
        title: "Si ipotizza rapimento da parte della POK",
        start: new Date(2014, 1, 20, 17, 30)
      },
      {
        id: 18,
        content: "Arrivo esperti",
        title: "Arrivono gli esperti di sicurezza di Tethys e gli ultimi dipendenti lasciano l'edificio",
        start: new Date(2014, 1, 20, 18),
        type: 'point'
      },
      {
        id: 19,
        content: "Intervista",
        title: "Edvard Vann viene intervistato",
        start: new Date(2014, 1, 20, 19),
        end: new Date(2014, 1, 20, 20)
      },
      {
        id: 20,
        content: "Trasferimento presidente",
        title: "Il presidente Kapelou viene trasferito in un luogo sicuro",
        start: new Date(2014, 1, 20, 20)
      },
      {
        id: 21,
        content: "Conferma rapimento",
        title: "Il funzionario di Kronos ha confermato il rapimento di 14 dipendenti",
        start: new Date(2014, 1, 20, 20),
        end: new Date(2014, 1, 20, 22)
      },
      {
        id: 22,
        title: "La polizia di Tethys è arrivata ad Abila",
        start: "2014-1-20 22:00",
        end: new Date(2014, 1, 20, 23),
        type: "point"
      },
      {
        id: 23,
        content: "Conferma falso allarme",
        title: "Il funzionario dell'Abila conferma era un falso allarme bomba ",
        start: new Date(2014, 1, 20, 22),
        end: new Date(2014, 1, 20, 23),
        type: 'point'
      },
      {
        id: 24,
        content: "Conferenza stampa Abila",
        title: " La polizia informa i giornalisti che quattro dei dipendenti della GAStech sono stati trovati durante la notte, lasciando 10 persone che si presume siano scomparse",
        start: new Date(2014, 1, 21, 9)
      },
      {
        id: 25,
        content: "Il CEO non è tra i rapiti",
        title: "Un portavoce di GAStech annuncia che il CEO Sten Sanjorge non è tra i dipendenti GAStech scomparsi",
        start: new Date(2014, 1, 21, 10, 16)
      },
      {id: 26, title: "POK consegna il messaggio", start: new Date(2014, 1, 21, 11), type: 'point'},
      {id: 27, content: "POK chiede un riscatto di 20 milioni di dollari", start: new Date(2014, 1, 21, 12)},
      {
        id: 28,
        content: "Fine notizie",
        start: new Date(2014, 1, 21, 12),
        end: new Date(2014, 1, 21, 13),
        type: "background"
      },
    ]);

    // Configuration for the Timeline
    const options = {
      start: new Date(2014, 1, 20, 7, 30),
      end: new Date(2014, 1, 20, 23, 59),
      width: '100%',
      height: '450px',
      margin: {
        item: 3
      },
      zoomMin: 3600000, //zoomin limitato a 1 ora
      zoomMax: 86400000, //zoomout limitato a 12 ore
      orientation: 'both'

    };
    // Create a Timeline
    const timeline = new Timeline(container, items, options);
    timeline.setOptions()
  }
}

</script>

<style>
div.timeline{
  text-align: center;
}
div.text{
  text-align: start;
}
.vis-item {
  border-color: #22226e;
  background-color: #5dc275;
}
.vis-time-axis{
  background: white;
}
</style>