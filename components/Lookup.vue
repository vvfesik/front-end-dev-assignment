<template>
  <div class="component-lookup row justify-content-center mt-6">
    <b-row>
      <b-col class="mb-3 mt-6">
        <b-form-input v-model="filter" placeholder="Type to Search" />
      </b-col>
    </b-row>
    <b-table striped hover :fields="fields" :items="table" :filter="filter" />
  </div>
</template>

<script>
  export default {
    name: 'Lookup',
    data() {
      return {
        table: [
          { idNumber: '277474-2016', name: 'DE LEON PARGA, JESUS, M', date: '11/20/16 0:00', address: '4400 W DAVIS ST' },
          { idNumber: '012715-2016', name: 'AKHTAR, SANA', date: '1/16/16 0:00', address: '5200 W DAVIS ST' },
          { idNumber: '277485-2015', name: 'JORDAN-GALINDO, DIANA', date: '11/29/15 0:00', address: '11000 HARRY HINES BLVD' },
          { idNumber: '276612-2015', name: 'NGUYEN, TUNG, THANH', date: '11/28/15 0:00', address: '10400 MARSH LN' },
          { idNumber: '278699-2016', name: 'NJUGUNA, NANCY, NJOKI', date: '11/21/16 0:00', address: '11800 GREENVILLE AVE' },
          { idNumber: '278555-2016', name: 'STEWART, ZATANYA', date: '11/21/16 0:00', address: '2800 CASEY ST' },
          { idNumber: '278235-2016', name: 'CITY OF DALLAS', date: '11/21/16 0:00', address: '9700 HARRY HINES BLVD' },
          { idNumber: '278642-2015', name: 'KEEPER, ALYSSA, M', date: '11/30/15 0:00', address: '4400 GREENVILLE AVE' },
          { idNumber: '278410-2015', name: 'WHITE, CHRISTIAN, LYNNAE', date: '11/30/15 0:00', address: '6000 S LANCASTER RD' },
          { idNumber: '278292-2016', name: 'RODRIGUEZ, ADRIAN, ARTURO', date: '11/21/16 0:00', address: '1900 S BUCKNER BLVD' },
          { idNumber: '170865-2017', name: 'CANO, FRANCISCO, JAVIER', date: '7/27/17 0:00', address: '500 W DAVIS ST' },
          { idNumber: '170865-2017', name: 'KIMBROUGH, MONIQUE', date: '7/27/17 0:00 ', address: '500 W DAVIS ST' },
          { idNumber: '218605-2017', name: 'ALVIZO, JOSE, HUMBERTO', date: '9/24/17 0:00', address: '10428 LOMBARDY LN' },
          { idNumber: '278349-2015', name: 'FRANKLIN, LISETTE', date: '11/30/15 0:00', address: '8400 S HAMPTON RD' },
          { idNumber: '280186-2016', name: 'WELLS, DAVIDA', date: '11/23/16 0:00', address: '8700 N CENTRAL EXPY' }
        ],
        fields: {
          idNumber: { label: 'ID Number' },
          name: { label: 'Name' },
          date: { label: 'Date', class: 'text-right' },
          address: { label: 'Address' }
        },
        filter: null
      }
    }
  }
</script>

<style>

</style>
