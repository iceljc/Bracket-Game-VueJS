<template>
  <b-container fluid='md'>
    <form @submit="getRes">
      <b-row>
        <!-- left brackets -->
        <b-col md="5">
          <b-row>
            <!-- round1 -->
            <b-col md="5">
              <b-row>
                <b-col class="group-team-left">
                  <span class="team-name-mobile" id="round">Round I - Division I</span>
                  <br class="mobile-show">
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
              </b-row>
              <div class="divider"></div>
              <b-row>
                <b-col class="group-team-left">
                  <span class="team-name-mobile" id="round">Round I - Division II</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 3</span>
                  <div class="team3">
                    <span class="team-id-left">3</span>
                    <select class="dropdown" name="seed3" v-model="team3" @change="getCandidate3($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                  </div>
                  <div class="group-team-divider-left"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team4">
                    <span class="team-id-left">4</span>
                    <select class="dropdown" name="seed" v-model="team4" @change="getCandidate4($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team 4</span>
                </b-col>
              </b-row>
            </b-col>

            <!-- round2 -->
            <b-col md="4" class="round2-col-left">
              <span class="team-name-mobile" id="round">Semi-final I</span>
              <br class="mobile-show">
              <span class="team-name-mobile">Team A</span>
              <b-row>
                <b-col class="round2-div-left">
                  <div class="team-left-1">
                    <select class="dropdown" name="seed12" v-model="team12" @change="getSemiFinalCandidate1($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal1.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList1">{{ team.name }}</option>
                    </select>
                  </div>
                </b-col>
              </b-row>
              <div class="group-team-divider-left-round2"></div>
              <span class="team-name-mobile">VS</span>
              <b-row>
                <b-col class="round2-div-left">
                  <div class="team-left-2">
                    <select class="dropdown" name="seed34" v-model="team34" @change="getSemiFinalCandidate2($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal2.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList2">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team B</span>
                </b-col>
              </b-row>
            </b-col>

            <!-- round3 -->
            <b-col md="3" class="round3-col-left">
              <span class="team-name-mobile" id="round">Final</span>
              <br class="team-name-mobile">
              <span class="team-name-mobile">Final Team 1</span>
              <div class="round3-team-left">
                <select class="dropdown" name="final1" v-model="finalCandidate1" @change="getFinalCandidate1($event)">
                    <option disabled value=""></option>
                    <option v-bind:value="semiFinal1.indexOf(team)" v-bind:key="team.id" v-for="team in getSemiFinalList1">{{ team.name }}</option>
                </select>
              </div>
            </b-col>
          </b-row>
        </b-col>

        <!-- center - champion -->
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

        <!-- right brackets -->
        <b-col md="5">
          <b-row>
            <b-col md="3" class="round3-col-right">
              <span class="team-name-mobile" id="round">Final</span>
              <br class="team-name-mobile">
              <span class="team-name-mobile">Final Team 2</span>
              <div class="round3-team-right">
                <select class="dropdown" name="final2" v-model="finalCandidate2" @change="getFinalCandidate2($event)">
                    <option disabled value=""></option>
                    <option v-bind:value="semiFinal2.indexOf(team)" v-bind:key="team.id" v-for="team in getSemiFinalList2">{{ team.name }}</option>
                </select>
              </div>
            </b-col>

            <b-col md="4" class="round2-col-right">
              <span class="team-name-mobile" id="round">Semi-final II</span>
              <br class="team-name-mobile">
              <span class="team-name-mobile">Team C</span>
              <b-row>
                <b-col class="round2-div-right">
                  <div class="team-right-1">
                    <select class="dropdown" name="seed56" v-model="team56" @change="getSemiFinalCandidate3($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal3.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList3">{{ team.name }}</option>
                    </select>
                  </div>
                </b-col>
              </b-row>
              <div class="group-team-divider-right-round2"></div>
              <span class="team-name-mobile">VS</span>
              <b-row>
                <b-col class="round2-div-right">
                  <div class="team-right-2">
                    <select class="dropdown" name="seed78" v-model="team78" @change="getSemiFinalCandidate4($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal4.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList4">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team D</span>
                </b-col>
              </b-row>
            </b-col>

            <b-col md="5">
              <b-row>
                <b-col class="group-team-right">
                  <span class="team-name-mobile" id="round">Round I - Division III</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 5</span>
                  <div class="team5">
                    <select class="dropdown" name="seed5" v-model="team5" @change="getCandidate5($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">5</span>
                  </div>
                  <div class="group-team-divider-right"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team6">
                    <select class="dropdown" name="seed6" v-model="team6" @change="getCandidate6($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">6</span>
                  </div>
                  <span class="team-name-mobile">Team 6</span>
                </b-col>
              </b-row>
              <div class="divider"></div>
              <b-row>
                <b-col class="group-team-right">
                  <span class="team-name-mobile" id="round">Round I - Division IV</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 7</span>
                  <div class="team7">
                    <select class="dropdown" name="seed7" v-model="team7" @change="getCandidate7($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">7</span>
                  </div>
                  <div class="group-team-divider-right"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team8">
                    <select class="dropdown" name="seed8" v-model="team8" @change="getCandidate8($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">8</span>
                  </div>
                  <span class="team-name-mobile">Team 8</span>
                </b-col>
              </b-row>
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
  name: 'EightBrackets',
  data() {
    return {
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
      team1: '',
      team2: '',
      team3: '',
      team4: '',
      team5: '',
      team6: '',
      team7: '',
      team8: '',
      team12: '',
      team34: '',
      team56: '',
      team78: '',
      finalCandidate1: '',
      finalCandidate2: '',
      team_champ: '',
      quarterFinal1 : [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      quarterFinal2: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      quarterFinal3: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      quarterFinal4: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      semiFinal1: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      semiFinal2: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      final: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
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
        seed5: this.team5,
        seed6: this.team6,
        seed7: this.team7,
        seed8: this.team8,
        champion: this.team_champ
      };
      this.$emit('get-res', res);
    },
    getCandidate1(event) {
      this.quarterFinal1[0].id = event.target.name;
      this.quarterFinal1[0].name = event.target.value;
    },
    getCandidate2(event) {
      this.quarterFinal1[1].id = event.target.name;
      this.quarterFinal1[1].name = event.target.value;
    },
    getCandidate3(event) {
      this.quarterFinal2[0].id = event.target.name;
      this.quarterFinal2[0].name = event.target.value;
    },
    getCandidate4(event) {
      this.quarterFinal2[1].id = event.target.name;
      this.quarterFinal2[1].name = event.target.value;
    },
    getCandidate5(event) {
      this.quarterFinal3[0].id = event.target.name;
      this.quarterFinal3[0].name = event.target.value;
    },
    getCandidate6(event) {
      this.quarterFinal3[1].id = event.target.name;
      this.quarterFinal3[1].name = event.target.value;
    },
    getCandidate7(event) {
      this.quarterFinal4[0].id = event.target.name;
      this.quarterFinal4[0].name = event.target.value;
    },
    getCandidate8(event) {
      this.quarterFinal4[1].id = event.target.name;
      this.quarterFinal4[1].name = event.target.value;
    },
    getSemiFinalCandidate1(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.semiFinal1[0].id = this.quarterFinal1[index].id;
      this.semiFinal1[0].name = this.quarterFinal1[index].name;
    },
    getSemiFinalCandidate2(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.semiFinal1[1].id = this.quarterFinal2[index].id;
      this.semiFinal1[1].name = this.quarterFinal2[index].name;
    },
    getSemiFinalCandidate3(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.semiFinal2[0].id = this.quarterFinal3[index].id;
      this.semiFinal2[0].name = this.quarterFinal3[index].name;
    },
    getSemiFinalCandidate4(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.semiFinal2[1].id = this.quarterFinal4[index].id;
      this.semiFinal2[1].name = this.quarterFinal4[index].name;
    },
    getFinalCandidate1(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.final[0].id = this.semiFinal1[index].id;
      this.final[0].name = this.semiFinal1[index].name;
    },
    getFinalCandidate2(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.final[1].id = this.semiFinal2[index].id;
      this.final[1].name = this.semiFinal2[index].name;
    }
  },
  computed: {
    getQuarterFinalList1() {
      return this.quarterFinal1.filter(team => team.name !== '');
    },
    getQuarterFinalList2() {
      return this.quarterFinal2.filter(team => team.name !== '');
    },
    getQuarterFinalList3() {
      return this.quarterFinal3.filter(team => team.name !== '');
    },
    getQuarterFinalList4() {
      return this.quarterFinal4.filter(team => team.name !== '');
    },
    getSemiFinalList1() {
      return this.semiFinal1.filter(team => team.name !== '');
    },
    getSemiFinalList2() {
      return this.semiFinal2.filter(team => team.name !== '');
    },
    getFinalList() {
      return this.final.filter(team => team.name !== '');
    }
  }
}
</script>

<style scoped>

  @media only screen and (min-width: 768px) {
    .team1, .team3, .team5, .team7, 
    .team-left-1, .team-right-1 {
      padding-bottom: 5px;
    }

    .team2, .team4, .team6, .team8, 
    .team-left-2, .team-right-2 {
      padding-top: 5px;
    }

    /* left */

    .team-id-left {
      margin-right: 10px;
    }

    .group-team-divider-left {
      min-height: 50px;
      border-top: 1px solid black;
      border-right: 1px solid black;
      border-bottom: 1px solid black;
    }

    .group-team-divider-left-round2 {
      min-height: 160px;
      border-top: 1px solid black;
      border-right: 1px solid black;
      border-bottom: 1px solid black;
    }

    .round2-div-left {
      padding-left: 0px;
    }

    .group-team-left {
      padding-right: 0px;
    }

    .round2-col-left {
      padding-top: 25px;
      padding-left: 0px;
      padding-right: 0px;
    }

    .round3-col-left {
      padding-left: 0px;
      padding-right: 0px;
    }

    .round3-team-left {
      padding-top: 100px;
      padding-bottom: 5px;
      border-bottom: 1px solid black;
    }

    /* right */
    .team-id-right {
      margin-left: 10px;
    }

    .group-team-divider-right {
      min-height: 50px;
      border-top: 1px solid black;
      border-left: 1px solid black;
      border-bottom: 1px solid black;
    }

    .group-team-divider-right-round2 {
      min-height: 160px;
      border-top: 1px solid black;
      border-left: 1px solid black;
      border-bottom: 1px solid black;
    }

    .group-team-right {
      padding-left: 0px;
    }

    .round2-div-right {
      padding-right: 0px;
    }

    .round2-col-right {
      padding-top: 25px;
      padding-left: 0px;
      padding-right: 0px;
    }

    .round3-col-right {
      padding-left: 0px;
      padding-right: 0px;
    }

    .round3-team-right {
      padding-top: 100px;
      padding-bottom: 5px;
      border-bottom: 1px solid black;
    }


    .divider {
      min-height: 50px;
    }

    .champ-div {
      padding-top: 55px;
    }

    .team-name-mobile, .mobile-show {
      display: none;
    }
  }

  
  @media only screen and (max-width: 767px) {
    select {
        width: 80px;
    }

    .group-team-left, .group-team-right, 
    .round2-col-left, .round2-col-right,
    .champ-div, .round3-col-left, .round3-col-right {
        margin-top: 5px;
        margin-bottom: 5px;
        /* border: 1px solid black; */
        -moz-box-shadow: 0 0 3px #ccc;
        -webkit-box-shadow: 0 0 3px #ccc;
        box-shadow: 0 0 3px #ccc;
    }

    .team1, .team2, .team3, .team4,
    .team5, .team6, .team7, .team8 {
      padding-top: 5px;
      padding-bottom: 5px;
    }

    .team-id-right, .team-id-left {
      display: none;
    }

    .round2-col-left, .round2-col-right {
      padding-top: 5px;
      padding-bottom: 5px;
    }

    .round3-team-left, .round3-team-right, .champ-div {
      padding-top: 5px;
      padding-bottom: 5px;
    }

    #round {
      font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    }
    
  }



  #download-btn {
    margin-top: 20px;
  }

  .dropdown {
      border-color: blue;
  }

  select {
      text-align: center;
      text-align-last: center;
  }

  option {
      text-align: center;
  }
    
</style>>