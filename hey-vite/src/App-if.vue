<script setup>
const depositAmt = 12000;
const interest = 10;
</script>

<template>
 <!-- <10000 = no interest
 10000-49999 =10%
 50000-99999 =20%
 >=100000 =25% -->

  <p>Deposit Amount: {{ depositAmt }}</p>
  <p v-if="depositAmt = 10000">Interest: {{ depositAmt }}</p>
  <p v-else-if="depositAmt > 10000">Interest: {{ depositAmt * interest }}</p>
  <p v-else-if="depositAmt >= 50000">Interest: {{ depositAmt * ( interest * 2 ) }}</p>
  <p v-else-if="depositAmt >= 99999">Interest: {{ depositAmt * ( interest * 2.5 ) }}</p>
  <p v-else>Interest: 0</p>
</template>

<style></style>
