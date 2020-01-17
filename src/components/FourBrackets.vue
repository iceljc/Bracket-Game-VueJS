<template>
  <b-container fluid="md">
      <form @submit="getRes">
          <b-row>
            <b-col md="5">
                <b-row>
                    <b-col md="6" class="group-team-left">
                        <span class="team-name-mobile" id="round">Round I</span><br>
                        <span class="team-name-mobile">Team 1</span>
                        <div class="team1">
                            <span class="team-id-left">1</span>
                            <select class="dropdown" name="seed1" v-model="team1" @change="getCandidate1($event)">
                                <option disabled value=""></option>
                                <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                            </select>
                        </div>
                        <div class="group-team-divider-left"></div>
                        <span class="team-name-mobile">VS</span>
                        <div class="team2">
                            <span class="team-id-left">2</span>
                            <select class="dropdown" name="seed2" v-model="team2" @change="getCandidate2($event)">
                                <option disabled value=""></option>
                                <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                            </select>
                        </div>
                        <span class="team-name-mobile">Team 2</span>
                    </b-col>
                    
                    <b-col md="6" class="round2-div-left">
                        <span class="team-name-mobile" id="round">Final</span><br>
                        <span class="team-name-mobile">Final Team 2</span>
                        <div class="round2-team-left">
                            <select class="dropdown" name="seed12" v-model="team12" @change="getFinalCandidate1($event)">
                                <option disabled value=""></option>
                                <option v-bind:value="round2pos1.indexOf(team)" v-bind:key="team.id" v-for="team in getList1">{{ team.name }}</option>
                            </select>
                        </div>
                    </b-col>
                </b-row>
            </b-col>

            <b-col md="2">
                <div class="champ-div">
                    <span class="champ-span" id="round">Champion</span>
                    <div class="champ-dropdown">
                        <select class="dropdown" name="selected_team" v-model="team_champ">
                            <option disabled value=""></option>
                            <option v-bind:value="team.id" v-bind:key="team.id" v-for="team in getFinalList">{{ team.name }}</option>
                        </select>
                    </div>
                </div>
            </b-col>

            <b-col md="5">
                <b-row>
                    <b-col md="6" class="round2-div-right">
                        <span class="team-name-mobile" id="round">Final</span><br>
                        <span class="team-name-mobile">Final Team 2</span>
                        <div class="round2-team-right">
                            <select class="dropdown" name="seed34" v-model="team34" @change="getFinalCandidate2($event)">
                                <option disabled value=""></option>
                                <option v-bind:value="round2pos2.indexOf(team)" v-bind:key="team.id" v-for="team in getList2">{{ team.name }}</option>
                            </select>
                        </div>
                    </b-col>
                    <b-col md="6" class="group-team-right">
                        <span class="team-name-mobile" id="round">Round I</span><br>
                        <span class="team-name-mobile">Team 3</span>
                        <div class="team3">
                            <select class="dropdown" name="seed3" v-model="team3" @change="getCandidate3($event)">
                                <option disabled value=""></option>
                                <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                            </select>
                            <span class="team-id-right">3</span>
                        </div>
                        <div class="group-team-divider-right"></div>
                        <span class="team-name-mobile">VS</span>
                        <div class="team4">
                            <select class="dropdown" name="seed4" v-model="team4" @change="getCandidate4($event)">
                                <option disabled value=""></option>
                                <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                            </select>
                            <span class="team-id-right">4</span>
                        </div>
                        <span class="team-name-mobile">Team 4</span>
                    </b-col>
                </b-row>                
            </b-col>
        </b-row>
        <div id="download-btn">
            <b-button variant="danger" type="submit">Download</b-button>
        </div>
      </form>
  </b-container>
</template>

<script>

export default {
  name: 'FourBrackets',
  data() {
      return {
          team1: '',
          team2: '',
          team3: '',
          team4: '',
          team12: '',
          team34: '',
          team_champ: '',
          allTeams: [
              {'id':1, name:'Falcons'},
              {'id':2, name:'Ravens'},
              {'id':3, name:'Bills'},
              {'id':4, name:'Bears'},
              {'id':5, name:'Browns'},
              {'id':6, name:'Lions'},
              {'id':7, name:'Texans'},
              {'id':8, name:'Colts'},
              {'id':9, name:'Rams'},
              {'id':10, name:'Jets'},
              {'id':11, name:'Giants'},
              {'id':12, name:'49ers'},
              {'id':13, name:'Titans'},
              {'id':14, name:'Chiefs'},
              {'id':15, name:'Packers'},
              {'id':16, name:'Pathers'},
          ],
          round2pos1: [
              {'id': '1', name: ''},
              {'id': '2', name: ''}
          ],
          round2pos2: [
              {'id': '1', name: ''},
              {'id': '2', name: ''}
          ],
          final: [
              {'id': '1', name: ''},
              {'id': '2', name: ''}
          ]
      }
  },
  methods: {
      getRes(e) {
          e.preventDefault();
          const res = {
              seed1: this.team1,
              seed2: this.team2,
              seed3: this.team3,
              seed4: this.team4,
              champion: this.team_champ
          };
          this.$emit('get-res', res);
      },
      getCandidate1(event) {
          this.round2pos1[0].id = event.target.name;
          this.round2pos1[0].name = event.target.value;
      },
      getCandidate2(event) {
          this.round2pos1[1].id = event.target.name;
          this.round2pos1[1].name = event.target.value;
      },
      getCandidate3(event) {
          this.round2pos2[0].id = event.target.name;
          this.round2pos2[0].name = event.target.value;
      },
      getCandidate4(event) {
          this.round2pos2[1].id = event.target.name;
          this.round2pos2[1].name = event.target.value;
      },
      getFinalCandidate1(event) {
          let index = event.target.value;
          if (typeof index == "string") {
              index = Number(index);
          }
          this.final[0].id = this.round2pos1[index].id;
          this.final[0].name = this.round2pos1[index].name;
      },
      getFinalCandidate2(event) {
          let index = event.target.value;
          if (typeof index == "string") {
              index = Number(index);
          }
          this.final[1].id = this.round2pos2[index].id;
          this.final[1].name = this.round2pos2[index].name;
      }
  },
  computed: {
      getList1() {
          return this.round2pos1.filter(team => team.name !== '');
      },
      getList2() {
          return this.round2pos2.filter(team => team.name !== '');
      },
      getFinalList() {
          return this.final.filter(team => team.name !== '');
      }
  }
}
</script>

<style scoped>

    @media only screen and (min-width: 768px) {

        .group-team-divider-left {
            min-height: 50px;
            border-top: 1px solid black;
            border-right: 1px solid black;
            border-bottom: 1px solid black;
        }

        .group-team-divider-right {
            min-height: 50px;
            border-top: 1px solid black;
            border-left: 1px solid black;
            border-bottom: 1px solid black;
        }

        .team-id-left {
            margin-right: 10px;
        }

        .group-team-left {
            padding-right: 0px;
        }

        .round2-div-left {
            padding-left: 0px;
        }

        .round2-team-left {
            padding-top: 25px;
            padding-bottom: 5px;
            border-bottom: 1px solid black;
        }

        .team1, .team3 {
            padding-bottom: 5px;
        }

        .team2, .team4 {
            padding-top: 5px;
        }

        .team-id-right {
            margin-left: 10px;
        }

        .group-team-right {
            padding-left: 0px;
        }

        .round2-div-right {
            padding-right: 0px;
        }

        .round2-team-right {
            padding-top: 25px;
            padding-bottom: 5px;
            border-bottom: 1px solid black;
        }

        .team-name-mobile {
            display: none;
        }
    }

    @media only screen and (max-width: 767px) {
        select {
            width: 80px;
        }

        .group-team-left, .group-team-right, 
        .champ-div, .round2-div-left, .round2-div-right {
            margin-top: 5px;
            margin-bottom: 5px;
            /* border: 1px solid black; */
            -moz-box-shadow: 0 0 3px #ccc;
            -webkit-box-shadow: 0 0 3px #ccc;
            box-shadow: 0 0 3px #ccc;
        }

        .team1, .team2, .team3, .team4 {
            padding-top: 5px;
            padding-bottom: 5px;
        }

        .team-id-right, .team-id-left {
            display: none;
        }

        .round2-team-left, .round2-team-right, .champ-div {
            padding-top: 5px;
            padding-bottom: 5px;
        }

        .champ-span, .champ-dropdown {
            vertical-align: middle;
        }

        #round {
            font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
        }

    }

    .dropdown {
        border-color: blue;
    }

    #download-btn {
        margin-top: 20px;
    }

    select {
        text-align: center;
        text-align-last: center;
    }

    option {
        text-align: center;
    }

    
</style>>