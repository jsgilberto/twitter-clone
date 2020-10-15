<template>
<b-form @submit="onSubmit">
  <b-form-group
    id="input-group-1"
    label="Tweet"
    label-for="input-1"
  >
    <b-form-textarea
      v-model="form.tweet"
      id="input-1"
      type="text"
      required
      placeholder="Write something..."
      rows="3"
      max-rows="6"
    >
    </b-form-textarea>
  </b-form-group>
  <b-form-select v-model="form.selected" :options="tweetTypes" class="mb-3"></b-form-select>
  <b-button type="submit" variant="primary">Submit</b-button>
</b-form>
</template>

<script>
export default {
  name: "NewTweet",
  data() {
    return {
      form: {
        tweet: "",
        selected: null
      },
      tweetTypes: [
        {value: null, text: 'Please select an option'},
        {value: 'draft', text: 'Draft'},
        {value: 'instant', text: 'Instant Tweet'}
      ]
    }
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      console.log(JSON.stringify(this.form));
      this.$emit('new-tweet', this.form);
      this.reset();
    },
    reset() {
      this.form.tweet = "";
      this.form.selected = null;
    }
  }
}
</script>

<style scoped lang="scss">

</style>