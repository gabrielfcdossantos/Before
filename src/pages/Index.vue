<template>
  <q-page class="flex flex-center">
    <q-dialog v-model="alert">
      <q-card>
        <q-card-section>
          <div class="text-h6">Confirmação</div>
        </q-card-section>

        <q-card-section v-if="this.cantor === '100' && this.verificaCpf !== 0">
          <q-avatar>
            <img src="../statics/rita.png">
          </q-avatar>
          Parabéns você votou para a Rita Lee na premiação musical
        </q-card-section>
        <q-card-section v-if="this.cantor === '101' && this.verificaCpf !== 0">
          <q-avatar>
            <img src="../statics/cartola.png">
          </q-avatar>
           Parabéns você votou para o Cartola na premiação musical
        </q-card-section>
        <q-card-section v-if="this.cantor === '102' && this.verificaCpf !== 0">
          <q-avatar>
            <img src="../statics/ney.png">
          </q-avatar>
          Parabéns você votou para o Ney Matogrosso na premiação musical
        </q-card-section>
        <q-card-section v-if="this.cantor === '103' && this.verificaCpf !== 0">
          <q-avatar color="red" text-color="white" icon="sentiment_very_dissatisfied" />
          Desculpe Infelizmente não será possivel votar nesse artista. Aperte em OK e escolha outro.
        </q-card-section>
        <q-card-section v-if="this.cantor !== '103' && this.cantor !== '102' && this.cantor !== '101' && this.cantor !== '100' && this.verificaCpf !== 0">
          <q-avatar color="red" text-color="white" icon="sentiment_very_dissatisfied" />
          Infelizmente não foi escolhido um numero válido. Seu voto foi considerado nulo.
        </q-card-section>
        <q-card-section v-if="this.verificaCpf === 0">
          <q-avatar color="red" text-color="white" icon="sentiment_very_dissatisfied" />
          Esse CPF já foi utilizado.
        </q-card-section>
        <q-card-actions align="right">
          <q-btn flat label="OK" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
    <section class="column borda">
      <div class="textoCorpo">
        <span>Escolha seu artista favorito e vote.</span>
      </div>
      <div class="fotos row">
        <div class="artista column">
          <div class="nome">
            <span>rita lee</span>
          </div>
          <div class="">
            <img class="imagem" src="../statics/rita.png" alt="">
          </div>
          <div class="row numVotos">
            <span>votos: {{this.numVotosRita}}</span>
             <q-separator style="width:2px;" vertical inset />
            <span>{{this.percentRita}} %</span>
          </div>
          <div class="numeroCandidato">
            <span>#100</span>
          </div>
        </div>
        <div class="artista column">
          <div class="nome">
            <span>cartola</span>
          </div>
          <div class="">
            <img class="imagem" src="../statics/cartola.png" alt="">
          </div>
          <div class="row numVotos">
            <span>votos: {{this.numVotosCartola}}</span>
            <q-separator style="width:2px;" vertical inset />
            <span>{{this.percentCartola}} %</span>
          </div>
          <div class="numeroCandidato">
            <span>#101</span>
          </div>
        </div>
        <div class="artista column">
          <div class="nome">
            <span>n.matogrosso</span>
          </div>
          <div class="">
            <img class="imagem" src="../statics/ney.png" alt="">
          </div>
          <div class="row numVotos">
            <span>votos: {{this.numVotosNey}}</span>
            <q-separator style="width:2px;" vertical inset />
            <span>{{this.percentNey}} %</span>
          </div>
          <div class="numeroCandidato">
            <span>#102</span>
          </div>
        </div>
        <div class="artista column">
          <div class="nome">
            <span>anita</span>
          </div>
          <div class="">
            <img class="imagem" src="../statics/anita.png" alt="">
          </div>
          <div class="row numVotos">
            <span>votos: {{this.numVotosAnita}}</span>
            <q-separator style="width:2px;" vertical inset />
            <span>{{this.percentAnita}} %</span>
          </div>
          <div class="numeroCandidato">
            <span>#103</span>
          </div>
        </div>
        <div class="artista column">
          <div class="nome">
            <span>nulo</span>
          </div>
          <div class="">
            <img class="imagem" src="../statics/nulo.png" alt="">
          </div>
          <div class="numVotos row">
            <span>votos: {{this.numVotosNulo}}</span>
          </div>
        </div>
      </div>
      <div class="voto row">
        <q-input outlined v-model="cantor" label="Escolha seu numero" mask="###" style="width:340px;" />
        <q-input outlined v-model="cpf" label="Digite seu CPF" mask="###.###.###-##" style="width:428px;" />
        <q-btn @click="votar ()" class="botao" label="Votar" style="width:175px;" />
      </div>
    </section>
  </q-page>
</template>

<style>
.borda{
}
.botao{
  background: #ff4700;
  color: #FFFFFF;
  font-family: Montserrat;
  font-style: normal;
  font-weight: 600;
  font-size: 18px;
  line-height: 22px;
  margin-right: 60px;
}
.fotos{
  justify-content: space-between;
}
.voto{
  justify-content: space-between;
  margin-top: 50px;
}
.artista{
  margin-right: 60px;
  padding: 10px 10px 20px 10px;
  border: 1px solid #BFBFBF;
  background-color: white;
  box-shadow: 10px 10px 5px #aaaaaa;
  border-radius:20px 20px 20px 20px;
}
.numeroCandidato{
  width: 150px;
  text-align: center;
  font-weight: bold;
}
.numVotos{
  width: 150px;
  justify-content: space-between;
  text-transform: uppercase;
  font-weight: bold;
  font-size: 16px;
  font-family: Montserrat;
  color: #AAAAAA;
}
.nome{
  width: 150px;
  text-align: center;
  font-family: Montserrat;
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 18px;
  /* identical to box height, or 112% */
  text-transform: uppercase;
}
.imagem{
  height: 150px;
  width: 150px;
}
.textoCorpo{
  font-family: Montserrat;
  font-style: normal;
  font-weight: bold;
  font-size: 36px;
  line-height: 44px;
  /* identical to box height */
  text-align: center;
  margin-top: 59px;
  margin-bottom: 59px;
}
</style>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      cantor: '',
      cpf: '',
      listCpf: [],
      numVotosRita: 0,
      idRita: '100',
      percentRita: 0,
      numVotosCartola: 0,
      idCartola: '101',
      percentCartola: 0,
      numVotosNey: 0,
      idNey: '102',
      percentNey: 0,
      numVotosAnita: 0,
      idAnita: '103',
      percentAnita: 0,
      numVotosNulo: 0,
      idNulo: '104',
      percentNulo: 0,
      totalVotos: 0,
      alert: false,
      verificaCpf: 1
    }
  },
  methods: {
    votar () {
      if (this.listCpf.indexOf(this.cpf) === -1) {
        if (this.cantor === this.idRita) {
          console.log('entrou')
          this.listCpf.push(this.cpf)
          this.verificaCpf = this.verificaCpf + 1
          this.numVotosRita = this.numVotosRita + 1
          console.log('numero de votos da rita lee:' + this.numVotosRita)
          this.totalVotos = this.numVotosRita + this.numVotosCartola + this.numVotosNey
          this.percentRita = (this.numVotosRita * 100) / this.totalVotos
          this.percentCartola = (this.numVotosCartola * 100) / this.totalVotos
          this.percentNey = (this.numVotosNey * 100) / this.totalVotos
          this.percentAnita = (this.numVotosAnita * 100) / this.totalVotos
        }
        if (this.cantor === this.idCartola) {
          console.log('entrou')
          this.listCpf.push(this.cpf)
          this.verificaCpf = this.verificaCpf + 1
          this.numVotosCartola = this.numVotosCartola + 1
          console.log('numero de votos do cartola:' + this.numVotosCartola)
          this.totalVotos = this.numVotosRita + this.numVotosCartola + this.numVotosNey
          this.percentRita = (this.numVotosRita * 100) / this.totalVotos
          this.percentCartola = (this.numVotosCartola * 100) / this.totalVotos
          this.percentNey = (this.numVotosNey * 100) / this.totalVotos
          this.percentAnita = (this.numVotosAnita * 100) / this.totalVotos
        }
        if (this.cantor === this.idNey) {
          console.log('entrou')
          this.listCpf.push(this.cpf)
          this.verificaCpf = this.verificaCpf + 1
          this.numVotosNey = this.numVotosNey + 1
          console.log('numero de votos do Ney Matogrosso:' + this.numVotosNey)
          this.totalVotos = this.numVotosRita + this.numVotosCartola + this.numVotosNey
          this.percentRita = (this.numVotosRita * 100) / this.totalVotos
          this.percentCartola = (this.numVotosCartola * 100) / this.totalVotos
          this.percentNey = (this.numVotosNey * 100) / this.totalVotos
          this.percentAnita = (this.numVotosAnita * 100) / this.totalVotos
        }
        if (this.cantor === this.idAnita) {
          console.log('entrou')
          this.verificaCpf = this.verificaCpf + 1
        }
        if (this.cantor !== this.idNey && this.cantor !== this.idCartola && this.cantor !== this.idRita && this.cantor !== this.idAnita) {
          console.log('entrou')
          this.listCpf.push(this.cpf)
          this.verificaCpf = this.verificaCpf + 1
          this.numVotosNulo = this.numVotosNulo + 1
          console.log('numero de votos Nulos:' + this.numVotosNulo)
        }
      } else {
        this.verificaCpf = this.verificaCpf * 0
      }
      console.log(this.listCpf)
      this.percentRita = parseFloat(this.percentRita.toFixed(2))
      this.percentCartola = parseFloat(this.percentCartola.toFixed(2))
      this.percentNey = parseFloat(this.percentNey.toFixed(2))
      this.alert = true
    }
  }
}
</script>
