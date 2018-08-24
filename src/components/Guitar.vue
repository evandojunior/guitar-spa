<template>
  <div class="box">
      <div v-for="guitar in guitars" :key="guitar.id">
        <a :href="guitar.id">
          <h4>{{guitar.model}}</h4>
          <figure>
            <img :src="guitar.img" class="guitar-pic"> 
          </figure>
          </a>
      </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      url: "./guitars-api.json",
      guitars:{}
    }
  },
  methods: {
    getData(){
      axios.get(this.url)
      .then(response => {
        console.log(response.data)
        this.guitars = response.data.guitars
        console.log(this.guitars)
      }).catch(error => {
        alert("Poha mano, falhou óh!")
      })
    }
  },
  mounted(){
    this.getData()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.guitar-pic {
  width: 220px;
  height: 80px;
}
.description {
  
  width: 220px;
  border: 1px solid red;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.box {
  display: flex;
  justify-content: center;
}
</style>
