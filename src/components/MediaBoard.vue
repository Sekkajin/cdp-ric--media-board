<template>
  <div class="mediaBoard">
    <p>Export de Gaia (?)</p>
    <p>Exemple : localcode=82549821&amp;businessUnit=LMFR</p>
    <div class="sep"></div>
    <p class="designProd">
      <span class="infoprod" >Ref : {{ medias[0].products[0].localcode }}</span>
      <span class="infoprod" > - Désignation : {{ medias[0].products[0].name }}</span>
      <span class="nomenc">Nomenc : ?? - ?? - ??</span>
    </p>
    <div class="mediaWrap">
        <div class="media" v-for="media in medias" :key="media.mediaId">
          <div class="media-infos media-infos-1">
          </div>
          <img :src="media.mediaUrl"/>
          <div class="media-infos media-infos-2">
            <p>{{ media.name }}</p>
          </div>
      </div>
    </div>
    <button id="printButton" @click="impress()">Imprimer</button>
  </div>
</template>

<script>
import mediasData from "../assets/response.json"

export default {
  name: 'MediaBoard',
  props: {
  },
  methods: {
      impress() {
          window.print();
      }
  },
  data () {
    return {
      medias : mediasData
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped media="print">
.sep{
  width:100%;
  height:0px;
  border:2px solid black;
  margin:5px 0 5px 0;
}

.mediaWrap{
  display:flex;
  flex-direction: row;
  justify-content: flex-start;
  flex-wrap: wrap;
}

.media {
  margin:5px;
}

img {
  max-width:200px;
}

.designProd{
  text-align:left;
}

.infoprod{
  font-weight: bold;
}

.nomenc{
  margin-left:20px;
}

#printButton{
  position:fixed;
  bottom:50px;
  right:50px;
  padding:5px 3px 5px 3px;
  border-radius: 10px;
  cursor:pointer;
}

@media print{
    #printButton{
        display: none;
    }
}
</style>
