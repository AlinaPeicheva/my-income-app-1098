<template>
  <div class="income-item">
      <div class="removeItem" @click="removeItem">x</div>
      <div class="desc">{{income.desc}}</div>
      <div class="price">${{income.value}}</div>
      <div class="date">{{ formattedDate }}</div>
  </div>
</template>

<script>
export default {
  emits: ["remove-item"],
    props: { income: Object },
    setup(props,{emit}) {
      let date = new Date(props.income.date)
      let day = date.getDate().toString().padStart(2, "0");
      let month = date.getMonth().toString().padStart(2, "0");
      let year = date.getFullYear()
      let formattedDate = day + '.' + month  + "." + year;

      function  removeItem() {
        emit("remove-item", props.income.id)
      }
        return {
          formattedDate,
          removeItem
        }
    }
}
</script>