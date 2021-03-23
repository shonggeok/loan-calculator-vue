<template>
  <div>
    <div class="form-group">
      <label for="monthlyInstalment">Monthly Instalment</label>
      <div class="input-group">
        <div class="input-group-prepend">
          <span class="input-group-text">RM</span>
        </div>
        <input
            class="form-control"
            disabled
            id="monthlyInstalment"
            name="monthly_instalment"
            placeholder="Monthly Instalment"
            type="text"
            v-model="monthlyInstalment"
        >
      </div>
    </div>

    <div class="form-group">
      <label for="totalInterestPayable">Total Interest Payable</label>
      <div class="input-group">
        <div class="input-group-prepend">
          <span class="input-group-text">RM</span>
        </div>
        <input
            class="form-control"
            disabled
            id="totalInterestPayable"
            name="total_interest_payable"
            placeholder="Total Interest Payable"
            type="text"
            v-model="totalInterestPayable"
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Result',
  props: [
      'monthlyInstalment',
      'totalInterestPayable',
  ],
}
</script>