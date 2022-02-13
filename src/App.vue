<template>
  <Navbar :totalIncome="state.totalIncome"/>
  <Form  @handle-data="handleData"/>
  <Income-list @remove-item="removeItem" :state='state' />
</template>

<script>
import Navbar from './components/Navbar.vue'
import Form from './components/Form.vue'
import {reactive , computed } from 'vue'
import IncomeList from './components/IncomeList.vue'

export default {
  name: 'App',
  components: {Navbar, Form, IncomeList},
    setup() {
      const state = reactive({
        income: [],
        totalIncome : computed(() => {
          let temp = 0;
          state.income.length > 0 ? state.income.map((el,i) => {
            temp += state.income[i].value
          }) : "";
          return temp;
        }),

        sortedIncome: computed(() => {
          let temp = []
          let income = state.income.slice(0)
          temp = income.sort((a,b) => b.date - a.date);
          return temp
        })
      
      })

      function handleData (data) {
        let d = data.date.split('-')
        let newD = new Date(d[0], d[1], d[2])

         state.income = [...state.income , {
           id: Date.now(),
           desc: data.desc,
           value: parseInt(data.value),
           date: newD.getTime()
         }]
      }

      function removeItem (id) {
          state.income = state.income.filter(el => el.id != id)
      }

      return {
        handleData,
        state,
        removeItem
      }
    }
}
</script>