<template>
  <b-container fluid="md" class="container">
    <b-row align="center">
      <b-col>
        <p id="title">{{ msg }}</p>
        <p>Developer: Jicheng Lu</p>
        <p id="hint">Instruction: Please select the number of brackets.</p>
      </b-col>
    </b-row>
    <br>
    <b-row align="center">
      <b-col>
        <MyForm v-on:select-num="postNum" /> 
      </b-col>
    </b-row>
    <br><br>
    <b-row align="center">
      <b-col>
        <div v-if="brackets === '4'">
          <FourBrackets v-on:get-res="getData" />
        </div>
        <div v-if="brackets === '8'">
          <EightBrackets v-on:get-res="getData" />
        </div>
        <div v-if="brackets === '16'">
          <SixteenBrackets v-on:get-res="getData" />
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import MyForm from './components/MyForm'
import FourBrackets from './components/FourBrackets'
import EightBrackets from './components/EightBrackets'
import SixteenBrackets from './components/SixteenBrackets'

function exportToJsonFile(jsonData) {
    let dataStr = JSON.stringify(jsonData);
    let dataUri = 'data:application/json;charset=utf-8,'+ encodeURIComponent(dataStr);
    let exportFileDefaultName = 'result.json';

    let linkElement = document.createElement('a');
    linkElement.setAttribute('href', dataUri);
    linkElement.setAttribute('download', exportFileDefaultName);
    linkElement.click();
}

export default {
  name: 'app',
  components: {
    MyForm,
    FourBrackets,
    EightBrackets,
    SixteenBrackets
  },
  data() {
    return {
      msg: "Welcome to the Bracket Game!",
      brackets: ''
    }
  },
  methods: {
    postNum(n) {
      this.brackets = n;
    },
    getData(obj) {
      var download = confirm("Do you want to download the result?");
      if (download) {
        const keys = Object.keys(obj);
        for (const key of keys) {
          if (obj[key].length === 0) {
            alert("Please fill in the blank space.");
            return;
          }
        }
        console.log('downloading...');
        // console.log(obj);
        exportToJsonFile(obj);
      } else {
        console.log(obj);
      }
    }
  },
}
</script>

<style>
  .container {
    padding-bottom: 30px;
    margin: auto;
  }

  @media only screen and (min-width: 577px) {
    #title {
      font-size: 30px;
    }

    #hint {
      font-size: 20px;
    }
  }

  @media only screen and (max-width: 576px) {
    #title {
      font-size: 20px;
    }

    #hint {
      font-size: 10px;
    }
  }

  #title {
    font-weight: bold;
  }

</style>
