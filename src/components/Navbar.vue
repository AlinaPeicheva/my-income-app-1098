<template>
  <div class="navbar">
      <nav>
          <h1>My Income</h1>
          <h2 class="total-income">${{ totalIncome }}</h2>
      </nav>
  </div>
</template>

<script>
export default {
    props: {
        totalIncome: Number
    }
}
</script>

