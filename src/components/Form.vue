<template>
  <div>
    <div class="form-group text-info">
      <label for="loanAmount">Loan Amount</label>
      <div class="input-group">
        <div class="input-group-prepend">
          <span class="input-group-text">RM</span>
        </div>
        <input
            class="form-control"
            id="loanAmount"
            inputmode="numeric"
            name="loan_amount"
            placeholder="Loan Amount"
            type="number"
            v-model="loanAmount"
            v-on:keyup="getInstalment"
        >
      </div>
    </div>

    <div class="form-group text-info">
      <label for="loanPeriod">Loan Period</label>
      <div class="input-group">
        <input
            class="form-control"
            id="loanPeriod"
            inputmode="numeric"
            name="loan_period"
            placeholder="Loan Period"
            type="number"
            v-model="loanPeriod"
            v-on:keyup="getInstalment"
        >
        <div class="input-group-append">
          <span class="input-group-text">Year(s)</span>
        </div>
      </div>
    </div>

    <div class="form-group text-info">
      <label for="interestRatePct">Interest Rate</label>
      <div class="input-group">
        <input
            class="form-control"
            id="interestRatePct"
            inputmode="numeric"
            name="interest_rate"
            placeholder="Interest Rate"
            step=".01"
            type="number"
            v-model="interestRate"
            v-on:keyup="getInstalment"
        >
        <div class="input-group-append">
          <span class="input-group-text">%</span>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
// import ProductsListItem from './ProductsListItem.vue';

export default {
  name: 'Form',
  data() {
    return {
      interestRate: '',
      loanAmount: '',
      loanPeriod: '',
    }
  },
  methods: {
    getInstalment() {
      this.$emit('getInstalment', this.loanAmount, this.loanPeriod, this.interestRate);
    },
  },
}
</script>

<style>
</style>
