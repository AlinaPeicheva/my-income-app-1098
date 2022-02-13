<template>
    <div class="title">
        <p>Add Income</p>
    </div>
    <form @submit.prevent="formHandler">
      <input type="text" id="desc" placeholder="Income" v-model="formData.desc">
      <input type="number" id="num" placeholder="Amount" v-model="formData.value">
      <input type="date" id="date" lang="fr-CA" v-model="formData.date">
      <input class="btn btn-outline-success" type="submit" value="Submit">
    </form>
</template>

<script>
import { reactive } from 'vue'

export default {
    emits: ["handle-data"],
    setup(props , {emit}) {
        const formData = reactive({
            desc: null,
            value:null,
            date: null
        })

        function formHandler(){
            emit("handle-data",{
                desc: formData.desc,
                value: formData.value,
                date: formData.date
            })

            formData.desc = null
            formData.value = null
            formData.date = null
        }

        return {
            formData,
            formHandler
        }
    }
}
</script>