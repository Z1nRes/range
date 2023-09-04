<template>
  <div class="wrapper">
    <div class="container">
      <div class="btn-toogle" @click="toogle">
        <span class="span span-active">Все года</span>
        <span class="span">Месяца</span>
      </div>
      <div v-if="type === 'years'">
        <Date-Years :years="years" :inputMin="inputMin" :inputMax="inputMax"/>
      </div>
      <div v-else>
        <Date-Years :years="months" :inputMin="inputMin" :inputMax="inputMax"/>
      </div>
    </div>
    </div>
</template>

<script>
import DateYears from './components/DateYears.vue';

export default {
  components: {
    DateYears,
  },
  data() {
    return {
      type: "years",
      inputMin: 0,
      inputMax: 9,
      years: [
                {
                    'id': '0', 
                    'title': '2014',
                    'year': '2014'
                },
                {
                    'id': '1', 
                    'title': '2015',
                    'year': '2015'
                },
                {
                    'id': '2', 
                    'title': '2016',
                    'year': '2016'
                },
                {
                    'id': '3', 
                    'title': '2017',
                    'year': '2017'
                },
                {
                    'id': '4', 
                    'title': '2018',
                    'year': '2018'
                },
                {
                    'id': '5', 
                    'title': '2019',
                    'year': '2019'
                },
                {
                    'id': '6', 
                    'title': '2020',
                    'year': '2020'
                },
                {
                    'id': '7', 
                    'title': '2021',
                    'year': '2021'
                },
                {
                    'id': '8', 
                    'title': '2022',
                    'year': '2022'
                },
                {
                    'id': '9', 
                    'title': '2023',
                    'year': '2023'
                },
            ],
      months: [
          {
              'id': '0', 
              'title': '2015',
              'year': '2015'
          },
          {
              'id': '1', 
              'title': 'фев',
              'year': '2015'
          },
          {
              'id': '2', 
              'title': 'мар',
              'year': '2015'
          },
          {
              'id': '3', 
              'title': 'май',
              'year': '2015'
          },
          {
              'id': '4', 
              'title': 'июн',
              'year': '2015'
          },
          {
              'id': '5', 
              'title': 'июл',
              'year': '2015'
          },
          {
              'id': '6', 
              'title': 'авг',
              'year': '2015'
          },
          {
              'id': '7', 
              'title': 'сен',
              'year': '2015'
          },
          {
              'id': '8', 
              'title': 'окт',
              'year': '2015'
          },
          {
              'id': '9', 
              'title': 'ноя',
              'year': '2015'
          },
          {
              'id': '10', 
              'title': 'дек',
              'year': '2015'
          },
          {
              'id': '11', 
              'title': '2016',
              'year': '2016'
          },
          {
              'id': '12', 
              'title': 'фев',
              'year': '2016'
          },
          {
              'id': '13', 
              'title': 'мар',
              'year': '2016'
          },
          {
              'id': '14', 
              'title': 'апр',
              'year': '2016'
          },
          {
              'id': '15', 
              'title': 'май',
              'year': '2016'
          },
          {
              'id': '16', 
              'title': 'июн',
              'year': '2016'
          },
          {
              'id': '17', 
              'title': 'июл',
              'year': '2016'
          },
          {
              'id': '18', 
              'title': 'авг',
              'year': '2016'
          },
          {
              'id': '19', 
              'title': 'сен',
              'year': '2016'
          },
          {
              'id': '20', 
              'title': 'окт',
              'year': '2016'
          },
          {
              'id': '21', 
              'title': 'ноя',
              'year': '2016'
          },
          {
              'id': '22', 
              'title': 'дек',
              'year': '2016'
          },
          {
              'id': '23', 
              'title': '2016',
              'year': '2016'
          },
      ]
    }
  },
  methods: {
    toogle() {
      if (this.type === 'years'){
        this.type = 'month'
        this.inputMin = 0
        this.inputMax = 24
      } else {
        this.type = 'years'
        this.inputMin = 0
        this.inputMax = 9
      }
      const span = document.querySelectorAll('.span')
      if(span[0].className === 'span span-active') {
        span[0].className = 'span'
        span[1].className = 'span span-active'
      } else {
        span[1].className = 'span'
        span[0].className = 'span span-active'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  width: 100%;
  font-family: Raleway;
  font-variant-numeric: lining-nums proportional-nums;
  font-style: normal;
  font-weight: 600;
  line-height: 18px;
}
.container {
  font-size: 14px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.btn-toogle{
  display: flex;
  flex-direction: column;
  align-items: start;
  cursor: pointer;
}
.span {
  color: #0167B3;
  opacity: 0.5;
}
.span-active {
  opacity: 1 !important;
}
</style>
