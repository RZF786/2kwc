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
      <v-card class="elevation-10">
        <v-card-text>
          <v-data-table :headers="subHeaders"
                        :items="subItems"
                        item-key="color"
                        hide-actions
                        class="elevation-10">
            <template slot="items" slot-scope="props">
              <td class="text-xs">{{ props.item.color }}</td>
              <td class="text-xs">{{ props.item.value }}</td>
            </template>
          </v-data-table>
        </v-card-text>
      </v-card>
    </template>
 </v-data-table>

</template>

<script>
  function format2(n, currency) {
      return currency + " " + n.toFixed(2).replace(/(\d)(?=(\d{3})+\.)/g, "$1,");
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
        subHeaders: [
          { text: 'Plan Payout Date', value: 'planPayoutDate' },
          { text: 'Plan Payout Amt', value: 'planPayoutAmt' },
          { text: 'Actual Payout Date', value: 'actualPayoutDate' },
          { text: 'Actual Payout Amt', value: 'actualPayoutAmt' },
        ],
        mainItems: [
          {
            value: false,
            name: 'Titanium 60 Series 2',
            contractNo: '200000012',
            contractAmt: format2(6000, "$"),
            paidUpAmt: format2(6000, "$"),
            maturityAmt: format2(7500, "$"),
            payoutAmtTD: format2(4000, "$"),
            balance: format2(3500, "$"),
            maturityDate: new Date('4/23/2018'),
            status: 'Active'
          },
          {
            value: false,
            name: 'Titanium 60 Series 2',
            contractNo: '200000013',
            contractAmt: format2(10000, "$"),
            paidUpAmt: format2(10000, "$"),
            maturityAmt: format2(12500, "$"),
            payoutAmtTD: format2(6000, "$"),
            balance: format2(6500, "$"),
            maturityDate: new Date('8/23/2018'),
            status: 'Active'
          },
          {
            value: false,
            name: 'Platinum 18',
            contractNo: '200000015',
            contractAmt: format2(10000, "$"),
            paidUpAmt: format2(10000, "$"),
            maturityAmt: format2(18000, "$"),
            payoutAmtTD: format2(18000, "$"),
            balance: format2(0, "$"),
            maturityDate: new Date('1/14/2018'),
            status: 'Fully Settled'
          }
        ],
        subItems: [
          { color: 'Red', value: '1' },
          { color: 'Green', value: '2' },
          { color: 'Blue', value: '3' },
          { color: 'Black', value: '4' }
        ]
      }
    }
  }
</script>