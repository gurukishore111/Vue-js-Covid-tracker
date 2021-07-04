<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!-- --------- -------- ------- -->

    <div class="shadow-md bg-green-100 p-10 text-center rounded">
      <h3 class="h3 text-3xl.textblue-900 font-bold mb-4">
        <i class="fas fa-procedures"></i>
        Cases
      </h3>

      <div class="text-2xl mb-4 text-gray-700">
        <span class="font-bold">
          New:
        </span>
        {{ numberWithCommas(stats.NewConfirmed) }}
      </div>
      <div class="text-2xl mb-4 text-gray-700">
        <span class="font-bold">
          Total:
        </span>
        {{ numberWithCommas(stats.TotalConfirmed) }}
      </div>
    </div>

    <!-- --------- -------- ------- -->
    <div class="shadow-md bg-green-200 p-10 text-center rounded">
      <h3 class="h3 text-3xl.textblue-900 font-bold mb-4">
        <i class="fas fa-feather"></i> Deaths
      </h3>

      <div class="text-2xl mb-4 text-gray-700">
        <span class="font-bold">
          New:
        </span>
        {{ numberWithCommas(stats.NewDeaths) }}
      </div>
      <div class="text-2xl mb-4 text-gray-700">
        <span class="font-bold">
          Total:
        </span>
        {{ numberWithCommas(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  name: 'DateBox',
  props: ['stats'],
  methods: {
    numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    },
  },
};
</script>
