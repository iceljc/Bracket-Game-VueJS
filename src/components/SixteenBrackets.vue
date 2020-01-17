<template>
  <b-container fluid='md'>
    <form @submit="getRes">
      <b-row>
        <!-- left brackets -->
        <b-col md="5">
          <b-row>
            <!-- round1 -->
            <b-col md="4">
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
                    <select class="dropdown" name="seed4" v-model="team4" @change="getCandidate4($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team 4</span>
                </b-col>
              </b-row>
              <div class="divider"></div>
              <b-row>
                <b-col class="group-team-left">
                  <span class="team-name-mobile" id="round">Round I - Division III</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 5</span>
                  <div class="team5">
                    <span class="team-id-left">5</span>
                    <select class="dropdown" name="seed5" v-model="team5" @change="getCandidate5($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                  </div>
                  <div class="group-team-divider-left"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team6">
                    <span class="team-id-left">6</span>
                    <select class="dropdown" name="seed6" v-model="team6" @change="getCandidate6($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team 6</span>
                </b-col>
              </b-row>
              <div class="divider"></div>
              <b-row>
                <b-col class="group-team-left">
                  <span class="team-name-mobile" id="round">Round I - Division IV</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 7</span>
                  <div class="team7">
                    <span class="team-id-left">7</span>
                    <select class="dropdown" name="seed7" v-model="team7" @change="getCandidate7($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                  </div>
                  <div class="group-team-divider-left"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team8">
                    <span class="team-id-left">8</span>
                    <select class="dropdown" name="seed8" v-model="team8" @change="getCandidate8($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team 8</span>
                </b-col>
              </b-row>
            </b-col>

            <!-- round2 -->
            <b-col md="3" class="round2-col-left">
              <b-row>
                <b-col class="round2-div-left">
                  <span class="team-name-mobile" id="round">Quarter-final I</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team A</span>
                  <div class="team-left-1">
                    <select class="dropdown" name="seedQuarter1" v-model="teamQuarter1" @change="getQuarterFinalCandidate1($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound1.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList1">{{ team.name }}</option>
                    </select>
                  </div>
                  <div class="group-team-divider-left-round2"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team-left-2">
                    <select class="dropdown" name="seedQuarter2" v-model="teamQuarter2" @change="getQuarterFinalCandidate2($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound2.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList2">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team B</span>
                </b-col>
              </b-row>
              <div class="divider-round2"></div>
              <b-row>
                <b-col class="round2-div-left">
                  <span class="team-name-mobile" id="round">Quarter-final II</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team C</span>
                  <div class="team-left-1">
                    <select class="dropdown" name="seedQuarter3" v-model="teamQuarter3" @change="getQuarterFinalCandidate3($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound3.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList3">{{ team.name }}</option>
                    </select>
                  </div>
                  <div class="group-team-divider-left-round2"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team-left-2">
                    <select class="dropdown" name="seedQuarter4" v-model="teamQuarter4" @change="getQuarterFinalCandidate4($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound4.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList4">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team D</span>
                </b-col>
              </b-row>
            </b-col>

            <!-- round3 -->
            <b-col md="3" class="round3-col-left">
              <b-row>
                <b-col class="round3-div-left">
                  <span class="team-name-mobile" id="round">Semi-final I</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team I</span>
                  <span class="team-name-mobile"></span>
                  <div class="team-left-1">
                    <select class="dropdown" name="seedSemi1" v-model="teamSemi1" @change="getSemiFinalCandidate1($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal1.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList1">{{ team.name }}</option>
                    </select>
                  </div>
                </b-col>
              </b-row>
              <div class="group-team-divider-left-round3"></div>
              <span class="team-name-mobile">VS</span>
              <b-row>
                <b-col class="round3-div-left">
                  <div class="team-left-2">
                    <select class="dropdown" name="seedSemi2" v-model="teamSemi2" @change="getSemiFinalCandidate2($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal2.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList2">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team J</span>
                </b-col>
              </b-row>
            </b-col>

            <!-- round4 -->
            <b-col md="2" class="round4-col-left">
              <span class="team-name-mobile" id="round">Final</span>
              <br class="mobile-show">
              <span class="team-name-mobile">Final Team 1</span>
              <div class="round4-team-left">
                <select class="dropdown" name="seedFinal1" v-model="finalCandidate1" @change="getFinalCandidate1($event)">
                    <option disabled value=""></option>
                    <option v-bind:value="semiFinal1.indexOf(team)" v-bind:key="team.id" v-for="team in getSemiFinalList1">{{ team.name }}</option>
                </select>
              </div>
            </b-col>
          </b-row>
        </b-col>

        <!-- center - champion -->
        <b-col md="2" class="champ-col">
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
            <!-- round4 -->
            <b-col md="2" class="round4-col-right">
              <span class="team-name-mobile" id="round">Final</span>
              <br class="mobile-show">
              <span class="team-name-mobile">Final Team 2</span>
              <div class="round4-team-right">
                <select class="dropdown" name="seedFinal2" v-model="finalCandidate2" @change="getFinalCandidate2($event)">
                    <option disabled value=""></option>
                    <option v-bind:value="semiFinal2.indexOf(team)" v-bind:key="team.id" v-for="team in getSemiFinalList2">{{ team.name }}</option>
                </select>
              </div>
            </b-col>

            <!-- round3 -->
            <b-col md="3" class="round3-col-right">
              <b-row>
                <b-col class="round3-div-right">
                  <span class="team-name-mobile" id="round">Semi-final II</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team K</span>
                  <div class="team-right-1">
                    <select class="dropdown" name="seedSemi3" v-model="teamSemi3" @change="getSemiFinalCandidate3($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal3.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList3">{{ team.name }}</option>
                    </select>
                  </div>
                </b-col>
              </b-row>
              <div class="group-team-divider-right-round3"></div>
              <span class="team-name-mobile">VS</span>
              <b-row>
                <b-col class="round3-div-right">
                  <div class="team-right-2">
                    <select class="dropdown" name="seedSemi4" v-model="teamSemi4" @change="getSemiFinalCandidate4($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="quarterFinal4.indexOf(team)" v-bind:key="team.id" v-for="team in getQuarterFinalList4">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team L</span>
                </b-col>
              </b-row>
            </b-col>

            <!-- round2 -->
            <b-col md="3" class="round2-col-right">
              <b-row>
                <b-col class="round2-div-right">
                  <span class="team-name-mobile" id="round">Quarter-final III</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team E</span>
                  <div class="team-right-1">
                    <select class="dropdown" name="seedQuarter5" v-model="teamQuarter5" @change="getQuarterFinalCandidate5($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound5.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList5">{{ team.name }}</option>
                    </select>
                  </div>
                  <div class="group-team-divider-right-round2"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team-right-2">
                    <select class="dropdown" name="seedQuarter6" v-model="teamQuarter6" @change="getQuarterFinalCandidate6($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound6.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList6">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team F</span>
                </b-col>
              </b-row>
              <div class="divider-round2"></div>
              <b-row>
                <b-col class="round2-div-right">
                  <span class="team-name-mobile" id="round">Quarter-final IV</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team G</span>
                  <div class="team-right-1">
                    <select class="dropdown" name="seedQuarter7" v-model="teamQuarter7" @change="getQuarterFinalCandidate7($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound7.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList7">{{ team.name }}</option>
                    </select>
                  </div>
                  <div class="group-team-divider-right-round2"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team-right-2">
                    <select class="dropdown" name="seedQuarter8" v-model="teamQuarter8" @change="getQuarterFinalCandidate8($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="secondRound8.indexOf(team)" v-bind:key="team.id" v-for="team in getSecondRoundList8">{{ team.name }}</option>
                    </select>
                  </div>
                  <span class="team-name-mobile">Team H</span>
                </b-col>
              </b-row>
            </b-col>

            <!-- round1 -->
            <b-col md="4">
              <b-row>
                <b-col class="group-team-right">
                  <span class="team-name-mobile" id="round">Round I - Division V</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 9</span>
                  <div class="team9">
                    <select class="dropdown" name="seed9" v-model="team9" @change="getCandidate9($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right" id="id9">9</span>
                  </div>
                  <div class="group-team-divider-right"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team10">
                    <select class="dropdown" name="seed10" v-model="team10" @change="getCandidate10($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">10</span>
                  </div>
                  <span class="team-name-mobile">Team 10</span>
                </b-col>
              </b-row>
              <div class="divider"></div>
              <b-row>
                <b-col class="group-team-right">
                  <span class="team-name-mobile" id="round">Round I - Division VI</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 11</span>
                  <div class="team11">
                    <select class="dropdown" name="seed11" v-model="team11" @change="getCandidate11($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">11</span>
                  </div>
                  <div class="group-team-divider-right"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team12">
                    <select class="dropdown" name="seed12" v-model="team12" @change="getCandidate12($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">12</span>
                  </div>
                  <span class="team-name-mobile">Team 12</span>
                </b-col>
              </b-row>
              <div class="divider"></div>
              <b-row>
                <b-col class="group-team-right">
                  <span class="team-name-mobile" id="round">Round I - Division VII</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 13</span>
                  <div class="team13">
                    <select class="dropdown" name="seed13" v-model="team13" @change="getCandidate13($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">13</span>
                  </div>
                  <div class="group-team-divider-right"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team14">
                    <select class="dropdown" name="seed14" v-model="team14" @change="getCandidate14($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">14</span>
                  </div>
                  <span class="team-name-mobile">Team 14</span>
                </b-col>
              </b-row>
              <div class="divider"></div>
              <b-row>
                <b-col class="group-team-right">
                  <span class="team-name-mobile" id="round">Round I - Division VIII</span>
                  <br class="mobile-show">
                  <span class="team-name-mobile">Team 15</span>
                  <div class="team15">
                    <select class="dropdown" name="seed15" v-model="team15" @change="getCandidate15($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">15</span>
                  </div>
                  <div class="group-team-divider-right"></div>
                  <span class="team-name-mobile">VS</span>
                  <div class="team16">
                    <select class="dropdown" name="seed16" v-model="team16" @change="getCandidate16($event)">
                        <option disabled value=""></option>
                        <option v-bind:value="team.name" v-bind:key="team.id" v-for="team in allTeams">{{ team.name }}</option>
                    </select>
                    <span class="team-id-right">16</span>
                  </div>
                  <span class="team-name-mobile">Team 16</span>
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
  name: 'SixteenBrackets',
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
      team9: '',
      team10: '',
      team11: '',
      team12: '',
      team13: '',
      team14: '',
      team15: '',
      team16: '',
      teamQuarter1: '',
      teamQuarter2: '',
      teamQuarter3: '',
      teamQuarter4: '',
      teamQuarter5: '',
      teamQuarter6: '',
      teamQuarter7: '',
      teamQuarter8: '',
      teamSemi1: '',
      teamSemi2: '',
      teamSemi3: '',
      teamSemi4: '',
      finalCandidate1: '',
      finalCandidate2: '',
      team_champ: '',
      secondRound1: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      secondRound2: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      secondRound3: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      secondRound4: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      secondRound5: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      secondRound6: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      secondRound7: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
      secondRound8: [
        {'id': '1', name: ''},
        {'id': '2', name: ''},
      ],
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
        seed9: this.team9,
        seed10: this.team10,
        seed11: this.team11,
        seed12: this.team12,
        seed13: this.team13,
        seed14: this.team14,
        seed15: this.team15,
        seed16: this.team16,
        champion: this.team_champ
      };
      this.$emit('get-res', res);
    },
    getCandidate1(event) {
      this.secondRound1[0].id = event.target.name;
      this.secondRound1[0].name = event.target.value;
    },
    getCandidate2(event) {
      this.secondRound1[1].id = event.target.name;
      this.secondRound1[1].name = event.target.value;
    },
    getCandidate3(event) {
      this.secondRound2[0].id = event.target.name;
      this.secondRound2[0].name = event.target.value;
    },
    getCandidate4(event) {
      this.secondRound2[1].id = event.target.name;
      this.secondRound2[1].name = event.target.value;
    },
    getCandidate5(event) {
      this.secondRound3[0].id = event.target.name;
      this.secondRound3[0].name = event.target.value;
    },
    getCandidate6(event) {
      this.secondRound3[1].id = event.target.name;
      this.secondRound3[1].name = event.target.value;
    },
    getCandidate7(event) {
      this.secondRound4[0].id = event.target.name;
      this.secondRound4[0].name = event.target.value;
    },
    getCandidate8(event) {
      this.secondRound4[1].id = event.target.name;
      this.secondRound4[1].name = event.target.value;
    },
    getCandidate9(event) {
      this.secondRound5[0].id = event.target.name;
      this.secondRound5[0].name = event.target.value;
    },
    getCandidate10(event) {
      this.secondRound5[1].id = event.target.name;
      this.secondRound5[1].name = event.target.value;
    },
    getCandidate11(event) {
      this.secondRound6[0].id = event.target.name;
      this.secondRound6[0].name = event.target.value;
    },
    getCandidate12(event) {
      this.secondRound6[1].id = event.target.name;
      this.secondRound6[1].name = event.target.value;
    },
    getCandidate13(event) {
      this.secondRound7[0].id = event.target.name;
      this.secondRound7[0].name = event.target.value;
    },
    getCandidate14(event) {
      this.secondRound7[1].id = event.target.name;
      this.secondRound7[1].name = event.target.value;
    },
    getCandidate15(event) {
      this.secondRound8[0].id = event.target.name;
      this.secondRound8[0].name = event.target.value;
    },
    getCandidate16(event) {
      this.secondRound8[1].id = event.target.name;
      this.secondRound8[1].name = event.target.value;
    },

    getQuarterFinalCandidate1(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal1[0].id = this.secondRound1[index].id;
      this.quarterFinal1[0].name = this.secondRound1[index].name;
    },
    getQuarterFinalCandidate2(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal1[1].id = this.secondRound2[index].id;
      this.quarterFinal1[1].name = this.secondRound2[index].name;
    },
    getQuarterFinalCandidate3(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal2[0].id = this.secondRound3[index].id;
      this.quarterFinal2[0].name = this.secondRound3[index].name;
    },
    getQuarterFinalCandidate4(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal2[1].id = this.secondRound4[index].id;
      this.quarterFinal2[1].name = this.secondRound4[index].name;
    },
    getQuarterFinalCandidate5(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal3[0].id = this.secondRound5[index].id;
      this.quarterFinal3[0].name = this.secondRound5[index].name;
    },
    getQuarterFinalCandidate6(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal3[1].id = this.secondRound6[index].id;
      this.quarterFinal3[1].name = this.secondRound6[index].name;
    },
    getQuarterFinalCandidate7(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal4[0].id = this.secondRound7[index].id;
      this.quarterFinal4[0].name = this.secondRound7[index].name;
    },
    getQuarterFinalCandidate8(event) {
      let index = event.target.value;
      if (typeof index == "string") {
          index = Number(index);
      }
      this.quarterFinal4[1].id = this.secondRound8[index].id;
      this.quarterFinal4[1].name = this.secondRound8[index].name;
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
    getSecondRoundList1() {
      return this.secondRound1.filter(team => team.name !== '');
    },
    getSecondRoundList2() {
      return this.secondRound2.filter(team => team.name !== '');
    },
    getSecondRoundList3() {
      return this.secondRound3.filter(team => team.name !== '');
    },
    getSecondRoundList4() {
      return this.secondRound4.filter(team => team.name !== '');
    },
    getSecondRoundList5() {
      return this.secondRound5.filter(team => team.name !== '');
    },
    getSecondRoundList6() {
      return this.secondRound6.filter(team => team.name !== '');
    },
    getSecondRoundList7() {
      return this.secondRound7.filter(team => team.name !== '');
    },
    getSecondRoundList8() {
      return this.secondRound8.filter(team => team.name !== '');
    },
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
    },
  }
}
</script>

<style scoped>
    @media only screen and (min-width: 768px) {

      @media screen and (min-width: 767px) and (max-width: 993px) {
        .team-id-left, .team-id-right {
          display: none;
        }
      }

      .team1, .team3, .team5, .team7, 
      .team9, .team11, .team13, .team15,
      .team-left-1, .team-right-1 {
        padding-bottom: 5px;
      }

      .team2, .team4, .team6, .team8, 
      .team10, .team12, .team14, .team16,
      .team-left-2, .team-right-2 {
        padding-top: 5px;
      }

      .divider {
        min-height: 50px;
      }

      .divider-round2 {
        min-height: 95px;
      }

      #id9 {
        margin-left: 15px;
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

      .group-team-left {
        padding-right: 0px;
      }

      .round2-col-left {
        padding-top: 25px;
        padding-right: 0px;
      }

      .round2-div-left {
        padding-left: 0px;
      }

      .group-team-divider-left-round3 {
        min-height: 320px;
        border-top: 1px solid black;
        border-right: 1px solid black;
        border-bottom: 1px solid black;
      }

      .round3-col-left {
        padding-top: 100px;
        padding-left: 0px;
        padding-right: 0px;
      }

      .round4-col-left {
        padding-top: 260px;
        padding-left: 0px;
        padding-right: 0px;
      }

      .round4-team-left {
        padding-bottom: 5px;
        border-bottom: 1px solid black;
      }

      .champ-div {
        padding-top: 180px;
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

      .round2-col-right {
        padding-top: 25px;
        padding-right: 0px;
      }

      .round2-div-right {
        padding-left: 0px;
      }

      .group-team-divider-right-round3 {
        min-height: 320px;
        border-top: 1px solid black;
        border-left: 1px solid black;
        border-bottom: 1px solid black;
      }

      .round3-col-right {
        padding-top: 100px;
        padding-left: 0px;
        padding-right: 0px;
      }

      .round4-col-right {
        padding-top: 260px;
        padding-left: 0px;
        padding-right: 0px;
      }

      .round4-team-right {
        padding-bottom: 5px;
        border-bottom: 1px solid black;
      }

      .team-name-mobile, .mobile-show {
        display: none;
      }
    }

    @media only screen and (max-width: 767px) {
      select {
        width: 80px;
      }

      .team-id-right, .team-id-left {
        display: none;
      }

      .group-team-left, .group-team-right, 
      .round2-div-left, .round2-div-right,
      .champ-div, .round3-col-left, .round3-col-right,
      .round4-col-left, .round4-col-right {
          margin-top: 5px;
          margin-bottom: 5px;
          /* border: 1px solid black; */
          -moz-box-shadow: 0 0 3px #ccc;
          -webkit-box-shadow: 0 0 3px #ccc;
          box-shadow: 0 0 3px #ccc;
      }

      .team1, .team2, .team3, .team4,
      .team5, .team6, .team7, .team8,
      .team9, .team10, .team11, .team12,
      .team13, .team14, .team15, .team16 {
        padding-top: 5px;
        padding-bottom: 5px;
      }

      .round3-team-left, .round3-team-right,
      .round4-team-left, .round4-team-right, .champ-div {
        padding-top: 5px;
        padding-bottom: 5px;
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