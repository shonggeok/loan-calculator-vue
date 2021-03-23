<template>
  <div class="container min-vh-100 min-vw-100 bg-dark">
    <div class="row min-vh-100">
      <div class="col-md-6 mx-auto my-auto">
        <div class="card bg-light">
          <div class="card-header text-center bg-info text-white">
            <h2>Home Loan Calculator</h2>
          </div>
          <div class="card-body font-weight-bold">
            <Form
                v-on:getInstalment="getInstalment"
            />
          </div>
          <div class="card-body font-weight-bold bg-white text-dark">
            <Result
                :monthlyInstalment="monthlyInstalment"
                :totalInterestPayable="totalInterestPayable"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Form from '../components/Form.vue';
import Result from '../components/Result.vue';

export default {
  name: 'Calculator',
  components: {
    Form,
    Result,
  },
  data() {
    return {
      monthlyInstalment: 0,
      totalInterestPayable: 0,
    };
  },
  methods: {
    getInstalment(loanAmount, loanPeriod, interestRate) {
      if (loanAmount !== ''
          && interestRate !== ''
          && loanPeriod !== ''
      ) {
        let P = loanAmount;
        let r = interestRate;
        let n = loanPeriod * 12;

        let M = this.pmt(r, n, P);
        let ip = (M * n) - P;

        this.monthlyInstalment = M.toFixed(2);
        this.totalInterestPayable = ip.toFixed(2);
      } else {
        this.monthlyInstalment = 0;
        this.totalInterestPayable = 0;
      }
    },
    pmt(rate, nper, pv) {
      /**
       * rate - Interest rate for the loan
       * nper - Total number of monthly payments for the loan
       * pv   - The present value; Also known as the principal
       */

      let r = rate / 1200;
      return r * -pv * Math.pow((1 + r), nper) / (1 - Math.pow((1 + r), nper));
    }
  }
}
</script>
