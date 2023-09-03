<template>
    <div>

        <div class="container">

            <div class="range-slider" list="list">
              <div class="progress"></div>
              <div>
                <div class="out-wrapper">
                  <div class="out out-min" for="inputMin">{{ inputValueMin }}</div>
                </div>
                <input name="inputMin" v-model="inputValueMin" @input="rangeFunc('min')" type="range" class="range-min" v-bind:min="inputMin" v-bind:max="inputMax" >
              </div>
              <div>
                <div class="out-wrapper">
                  <div class="out out-max" for="inputMax">{{ inputValueMax }}</div>
                </div>
                <input name="inputMax" v-model="inputValueMax" @input="rangeFunc('max')" type="range" class="range-max" v-bind:min="inputMin" v-bind:max="inputMax" >
              </div>
            </div>
            <div class="wrapper-list">
              <ListData :years="years" />
            </div>
        </div>

    </div>
</template>

<script>
import ListData from './ListData.vue';

export default {
    data() {
      return {
        inputValueMin: this.inputMin,
        inputValueMax: this.inputMax,
      }
    },
    props: ['years', 'inputMin', 'inputMax'],
    components: {
      ListData,
    },
    methods: {
      rangeFunc(el) {
        const range = document.querySelectorAll('.range-slider input');
        const progress = document.querySelector('.range-slider .progress');
        let gap = 1;
        const out = document.querySelectorAll('.out');
        let minrange = parseInt(range[0].value)
        let maxrange = parseInt(range[1].value)

        if(maxrange - minrange < gap) {
          if(el === 'min'){
            range[0].value = maxrange - gap
          } else {
            range[1].value = minrange + gap
          }
        } 


        out[0].style.left = progress.style.left = 100 - ((range[0].max - minrange) / (range[0].max - range[0].min)) * 100 + '%';
        out[1].style.right = progress.style.right = 100 - ((maxrange - range[1].min) / (range[1].max - range[1].min)) * 100 + '%';
        
      }
    }
}
</script>

<style lang="scss">

body {
  margin: 0;
  padding: 0;
  display: grid;
  place-items: center;
  min-height: 100vh;
  background: #222;
}

.container{
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
  height: 10em;
  background: #f7eeee;
  border-radius: 5em;
  margin: 3em;
}

.range-slider{

    position: relative;
    width: 85%;
    height: 5px;
    background: #ddd;
    outline: none;
    top: 1px;
    margin: 10px;

}

.range-slider input[type="range"] {
    position: absolute;
    top: -11px;
    left: -5px;
    width: 101%;
    appearance: none;
    pointer-events: none;
    background: transparent;
    outline: none;
}

.range-slider input::-webkit-slider-thumb {
    pointer-events: auto;
    appearance: none;
    width: 24px;
    height: 24px;
    background: #FFFFFF;
    border: 5px solid #5CADEA;
    border-radius: 50px;
}

.progress {
    left: 0%;
    right: 0%;
    height: 100%;
    background: #5CADEA;
    border-radius: 50px;
    position: absolute;
}


.wrapper-list{
  width: 86%;
}

.list{
    display: flex;
    justify-content: space-between;
    height: auto;
    overflow: hidden;
    margin-top: 16px; 
    width: 100%;
}



.out{
  position: relative;
  display: flex;
}
// .out::before{
//   content: '';
//   width: 50px;
//   height: 50px;
//   position: relative;
//   background: #222;
//   left: 2em;
// }

.out-min{
  position: absolute;
  top: -14em;
  left: 0%;
  background: #FFFFFF;
  width: 70px;
  height: 66px;
  filter: drop-shadow(0px 5px 15px rgba(14, 88, 143, 0.20));
}

.out-max{
  position: absolute;
  top: 1em;
  right: -6%;
  display: flex;
  justify-content: flex-end;
  background: #FFFFFF;
  width: auto;
  padding: 20px;
  filter: drop-shadow(0px 5px 15px rgba(14, 88, 143, 0.20));
  border-radius: 10px;
}

</style>