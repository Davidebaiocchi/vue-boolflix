<template>
  <header>
    <div class="left-section">
      <h1>
        Boolflix
      </h1>
    </div>

    <div class="right-section">
      <form action="">
        <input 
        type="text" 
        placeholder="Cerca film o serie Tv"
        v-model.trim="srcText">
        <button @click.prevent="$emit('startTest',srcText)">Cerca</button>
      </form>
    </div>
  </header>
</template>

<script>
export default {
  name : 'Header',
  data(){
    return{
      srcText : ''
    }
  }
}
</script>

<style lang="scss">
  header{
    position: fixed;
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
    background-color: #0d0d0d;
    height: 80px;
    padding: 0 20px;
    z-index: 2;
    .left-section{
      color: red;
      font-size: 25px;
    }
    .right-section{
      form{
        *{
          height: 40px;
          margin-right: 20px;
          cursor: pointer;
          background-color: red;
          color: white;
          border: 0;
          padding: 0 10px;
        }
        input {
          width: 200px;
          padding-left: 10px;
          font-size: 18px;
          background-color: #0d0d0d;
          border: 0;
          color: white;
          border-bottom: 2px solid rgb(0, 76, 255);
          text-align: center;
        }
      }
    }
  }
</style>