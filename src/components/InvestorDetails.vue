<template>
  <v-data-table :headers="mainHeaders"
                :items="mainItems"
                item-key="name"
                hide-actions
                expand
                class="elevation-4">
    <template slot="items" slot-scope="props">
      <tr @click="props.expanded = !props.expanded">
        <td class="text-xs-left">{{ props.item.name }}</td>
        <td class="text-xs-left">{{ props.item.contractNo }}</td>
        <td class="text-xs-left">{{ props.item.contractAmt }}</td>
        <td class="text-xs-left">{{ props.item.paidUpAmt }}</td>
        <td class="text-xs-left">{{ props.item.maturityAmt}}</td>
        <td class="text-xs-left">{{ props.item.payoutAmtTD}}</td>
        <td class="text-xs-left">{{ props.item.balance}}</td>
        <td class="text-xs-left">{{ props.item.maturityDate | moment("DD-MMM-YY") }}</td>
        <td class="text-xs-left">{{ props.item.status }}</td>
      </tr>
    </template>
    <template slot="expand" slot-scope="props">
      <v-container fluid grid-list-md>
        <v-layout row wrap>
          <v-flex d-flex xs12 sm6 md4>
            <v-data-table :headers="subPlanHeaders"
                          :items="subPlanItems"
                          item-key="planPayoutDate"
                          hide-actions
                          class="elevation-10">
              <template slot="items" slot-scope="props">
                <td class="text-xs">{{ props.item.planPayoutDate | moment("DD-MMM-YY")}}</td>
                <td class="text-xs">{{ props.item.planPayoutAmt }}</td>
              </template>
            </v-data-table>
          </v-flex>
          <v-flex d-flex xs12 sm6 md4>
            <v-data-table :headers="subActualHeaders"
                          :items="subActualItems"
                          item-key="actualPayoutDate"
                          hide-actions
                          class="elevation-10">
              <template slot="items" slot-scope="props">
                <td class="text-xs">{{ props.item.actualPayoutDate | moment("DD-MMM-YY")}}</td>
                <td class="text-xs">{{ props.item.actualPayoutAmt }}</td>
              </template>
            </v-data-table>
          </v-flex>
        </v-layout>  
      </v-container>
    </template>
  </v-data-table>
</template>

<script>
  function currency(n, symbol) {
      return symbol + " " + n.toFixed(2).replace(/(\d)(?=(\d{3})+\.)/g, "$1,");
  }

  export default {
    name:'InvestorDetails',
    data () {
      return {
        mainHeaders: [
          {
            text: 'Contract(s)',
            align: 'left',
            sortable: true,
            value: 'name'
            
          },
          { text: 'Contract No', value: 'contractNo' },
          { text: 'Contract Amt', value: 'contractAmt' },
          { text: 'Paid Up Amt', value: 'paidUpAmt' },
          { text: 'Maturity Amt', value: 'maturityAmt' },
          { text: 'Payout Amt ToDate', value: 'payoutAmtTD' },
          { text: 'Balance', value: 'balance' },
          { text: 'Maturity Date', value: 'maturityDate' },
          { text: 'Status', value: 'status' }
        ] ,
        subPlanHeaders: [
          { text: 'Plan Payout Date', value: 'planPayoutDate' },
          { text: 'Plan Payout Amt', value: 'planPayoutAmt' },
        ],
        subActualHeaders: [
          { text: 'Actual Payout Date', value: 'actualPayoutDate' },
          { text: 'Actual Payout Amt', value: 'actualPayoutAmt' },
        ],

        mainItems: [
          {
            value: false,
            name: 'Titanium 60 Series 2',
            contractNo: '200000012',
            contractAmt: currency(6000, "$"),
            paidUpAmt: currency(6000, "$"),
            maturityAmt: currency(7500, "$"),
            payoutAmtTD: currency(4000, "$"),
            balance: currency(3500, "$"),
            maturityDate: new Date('4/23/2018'),
            status: 'Active'
          },
          {
            value: false,
            name: 'Titanium 60 Series 2',
            contractNo: '200000013',
            contractAmt: currency(10000, "$"),
            paidUpAmt: currency(10000, "$"),
            maturityAmt: currency(12500, "$"),
            payoutAmtTD: currency(6000, "$"),
            balance: currency(6500, "$"),
            maturityDate: new Date('8/23/2018'),
            status: 'Active'
          },
          {
            value: false,
            name: 'Platinum 18',
            contractNo: '200000015',
            contractAmt: currency(10000, "$"),
            paidUpAmt: currency(10000, "$"),
            maturityAmt: currency(18000, "$"),
            payoutAmtTD: currency(18000, "$"),
            balance: currency(0, "$"),
            maturityDate: new Date('1/14/2018'),
            status: 'Fully Settled'
          }
        ],
        subPlanItems: [
          { 
            planPayoutDate: new Date('1/30/2018'),
            planPayoutAmt: currency(2300,"$") 
          },
          { planPayoutDate: 'Feb-2018', value: '2' },
          { planPayoutDate: 'Mar-2018', value: '3' },
          { planPayoutDate: 'Apr-2018', value: '4' },
          { planPayoutDate: 'May-2018', value: '1' },
          { planPayoutDate: 'Jun-2018', value: '2' },
          { planPayoutDate: 'Jul-2018', value: '3' },
          { planPayoutDate: 'Aug-2018', value: '4' }
        ],
        subActualItems: [
          { 
            actualPayoutDate: new Date('2/15/2018'),
            actualPayoutAmt: currency(1800,"$") 
          },
          { actualPayoutDate: 'Feb-2018', value: '2' },
          { actualPayoutDate: 'Mar-2018', value: '3' },
          { actualPayoutDate: 'Apr-2018', value: '4' },
          { actualPayoutDate: 'May-2018', value: '1' },
          { actualPayoutDate: 'Jun-2018', value: '2' },
          { actualPayoutDate: 'Jul-2018', value: '3' },
          { actualPayoutDate: 'Aug-2018', value: '4' }
        ]
      }
    }
  }
</script>