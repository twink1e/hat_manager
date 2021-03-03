<template>
<div>
  <md-field>
    <md-input type="file" accept="image/*" @change="onImageUpload"></md-input>
  </md-field>
</div>
</template>

<script>
export default {
name: "FileManager",
  data() {
  return {
    url: null
  }
  },
  methods: {
    onImageUpload: function (e) {
      console.log('invoke')
      const file = e.target.files[0];
      this.url = URL.createObjectURL(file);
      this.$root.$emit('fileUpload', this.url);
    }
  }
}
</script>

<style scoped>

</style>