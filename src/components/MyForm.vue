<template>
  <b-container fluid="md">
      <form @submit="postNum">
          <!-- <input type="text" v-model="form_num" name="number" placeholder="..."> -->
          <select name="number" id="number" v-model="selected">
              <option disabled value="">Please select one</option>
              <option value="4">4</option>
              <option value="8">8</option>
              <option value="16">16</option>
          </select>
          <br><br>
          <b-button variant="primary" type="submit">Confirm</b-button>
      </form>
  </b-container>
</template>

<script>

export default {
  name: 'MyForm',
  data() {
      return {
        selected: ''
      }
  },
  methods: {
      postNum(e) {
          e.preventDefault();
          this.$emit('select-num', this.selected);
      }
  }
}
</script>

<style scoped>
    #number {
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

