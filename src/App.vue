<template>
  <h1>Expanding cards</h1>
  <div class="container">
    <div class="panel" @click="handleClick(panel)" :class="{active: panel.active}" :style="{ backgroundImage: 'url(' + panel.src + ')' }" v-for="panel in panels">
      <p>{{ panel.title}}</p>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(206, 221, 239);
  margin-top: 60px;
  max-width: 700px;
  margin: auto;
}
body {
  background-color: rgb(7, 13, 89);
}
.container {
  display: flex;
  justify-content: center;
  height: 80vh;
}
.panel {
  flex: 0.1;
  position: relative;
  margin-right: 10px;
  border-radius: 4px;
  cursor: pointer;
  border: 3px solid rgb(206, 221, 239, 0.5);
  transition: flex 0.6s ease-in;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
.panel:before {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgb(7, 13, 89, 0.7);
  left: 0;
  top: 0;
  opacity: 1;
  transition: opacity 0.6s ease-in;
}
.panel p {
  position: absolute;
  opacity: 0;
  left: 10px;
  bottom: 10px;
  transition: opacity 0.5s ease 0.2s;
  background-color: rgb(7, 13, 89, 0.5);
  padding: 2px 6px;
  border-radius: 2px;
}

/* active */
.panel.active {
  flex: 0.5;
}
.panel.active p {
  opacity: 1;
}
.panel.active:before {
  opacity: 0;
}
</style>

<script>

export default {
  name: "App",
  components: {  },
  methods: {
    handleClick(panel) {
      // this.panels = this.panels.map(panel => panel.active = false)
      this.panels.forEach(element => {
        element.active = false
      });
      panel.active = true
    }
  },
  data() {
    return {
      panels: [{
        src: 'https://cdn.bmwblog.com/wp-content/uploads/2016/04/BMW-M2-high-quality-wallpapers-204.jpg',
        title: 'BMW',
        active: true,
        id: 1},
        {
        src: 'https://mercedes-benz-media.co.uk/assets/images/thumbnail-true/23809-Mercedes-AMGGTSSidewallpaperforiPad-Portrait.jpg',
        title: 'Mercedes',
        active: false,
        id: 2},
        {
        src: 'https://www.autocar.co.uk/sites/autocar.co.uk/files/styles/gallery_slide/public/images/car-reviews/first-drives/legacy/gtr-37.jpg?itok=QzZe_gDt',
        title: 'Nissan',
        active: false,
        id: 3},
        {
        src: 'https://i.pinimg.com/originals/0e/a2/39/0ea239fee74c98fb06d2f7b01f824f0e.jpg',
        title: 'Porsche'
        ,
        active: false,
        id: 4},
        {
        src: 'https://i.pinimg.com/originals/fb/37/0d/fb370d862ed7fa67f8763e0eb9ca4925.jpg',
        title: 'Lamborghini ',
        active: false,
        id: 5},]
    };
  },
};
</script>


