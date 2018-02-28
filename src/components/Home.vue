<template>
  <v-container fluid> 
    <v-layout column align-left>
      <data-table></data-table>
    </v-layout>
  </v-container>
</template>

<script>
  // import db from './firebaseInit'
  import DataTable from './DataTable'
  export default {
    name: 'home',
    components: {
      DataTable
    },
    data () {
      return {
        investors: [],
        loading: true
      }
    },
    created () {

      let investors = [
        {
          investorID: '008',
          name: 'Arthur Aztech',
          address: {
            blk: '1',
            street: 'Desert Road',
            unit: 'B1-01',
            country: 'Afghanistan',
            postcode: '1007900'
          },
          contracts: [
            {
              contractNum: "2000001493",
              plan: "Titanium 60 Series 2",
              contractAmt: 6000,
              maturityDate: new Date('8/14/2018'),
              maturityPayout: 6210,
              payoutPlan : [
                { 
                  planPayoutDate: new Date('3/1/2018'),
                  planPayoutAmt: 1000
                },
                { 
                  planPayoutDate: new Date('4/4/2018'),
                  planPayoutAmt: 1000
                },
                { 
                  planPayoutDate: new Date('5/5/2018'),
                  planPayoutAmt: 1000
                },
                { 
                  planPayoutDate: new Date('6/6/2018'),
                  planPayoutAmt: 1000
                },
                { 
                  planPayoutDate: new Date('7/7/2018'),
                  planPayoutAmt: 1000
                },
                { 
                  planPayoutDate: new Date('8/8/2018'),
                  planPayoutAmt: 1000
                },
              ],
              payoutActual : [
                { 
                  actualPayoutDate: new Date('3/3/2018'),
                  actualPayoutAmt: 1000,
                  chequeNum: "20031",
                  status: "cleared"
                },
                { 
                  actualPayoutDate: new Date('4/4/2018'),
                  actualPayoutAmt: 1000,
                  chequeNum: "20041",
                  status: "cleared"
                }
              ]

            }
          ]
        }
       
      ]

      this.investors = investors
      // db.collection('employees').orderBy('dept').get().then((querySnapshot) => {
      //   this.loading = false
      //   querySnapshot.forEach((doc) => {
      //     const data = {
      //       'id': doc.id,
      //       'employee_id': doc.data().employee_id,
      //       'name': doc.data().name,
      //       'dept': doc.data().dept,
      //       'position': doc.data().position
      //     }
      //     this.employees.push(data)
      //   })
      // })
    }
  }
</script>