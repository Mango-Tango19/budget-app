<template>
  <div class="total-value">
    balance:  {{ total }}
  </div>
</template>

<script>
export default {
    name: 'TotalBalance',
    props: {
        total: {
            type: Number,
            default: 0
        }
    }

}
</script>

<style scooped>
.total-value {
    font-size: 26px;
    text-transform: uppercase;
    padding: 20px;
    text-align: center;
}



</style>