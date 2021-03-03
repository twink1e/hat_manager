<template>
<div>
  <md-field>
    <label>Width</label>
    <md-input v-model="width" @change="onSizeChange"></md-input>
  </md-field>
  <md-field>
    <label>Height</label>
    <md-input v-model="height" @change="onSizeChange"></md-input>
  </md-field>
  <canvas ref="canvas" />
</div>
</template>

<script>
export default {
name: "DrawingBoard",
  data() {
    return {
      image: null,
      width: 130,
      height: 130,
    }
  },
  computed: {
    canvas: function () {
      return this.$refs['canvas'];
    },
    ctx: function () {
      return this.canvas.getContext('2d');
    }
  },
  mounted() {
    this.$root.$on('fileUpload', data => {
      this.url = data;
      this.drawImage(data);
      console.log(data);
    });
  },
  methods: {
    onSizeChange: function () {
      this.ctx.drawImage(this.image, 0, 0, this.width, this.height);
    },
    drawImage: function (url) {
      const image = new Image();
      this.image = image;
      image.src = url;
      const self = this;
      image.onload = function() {
        self.width = image.naturalWidth;
        self.height = image.naturalHeight;
        self.$nextTick(() => {
          self.ctx.drawImage(image, 0, 0);
        })

      }
    }
  }
}
</script>

<style scoped>

</style>