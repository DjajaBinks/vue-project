<template>
  <div class="hello">
    <div class="container">
      <div class="menu-item">
        <div class="menu-text">
          Tralalala
        </div>
      </div>
      <div class="menu-item menu-center">
          Justin Djaja
      </div>
      <div class="menu-item">
        <div class="menu-text">
          Tralalala
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
  display: flex;
  align-items: center;
  justify-content: space-around;
  margin-top: 10px;
}
.menu-item{
  flex: 1;
  text-align: center;
  color: #707070;
}
.menu-text{
  font-size: 20px;
  color: #818181;
  cursor: pointer;
  padding: 10px;
  /* border-bottom: 2px solid #080808; */
}
.menu-text:hover{
  border-bottom: 2px solid 	#eaeaea;
}
.menu-center{
  font-size: 36px;
  color: #eaeaea;
}
</style>
