<template>
  <v-data-table
    :headers="headers"
    :items="items"
    class="elevation-1"
  >
    <template slot="headerCell" slot-scope="props">
      <v-tooltip bottom>
        <span slot="activator">
          {{ props.header.text }}
        </span>
        <span>
          {{ props.header.text }}
        </span>
      </v-tooltip>
    </template>
    <template slot="items" slot-scope="props">
      <td>{{ props.item.name }}</td>
      <td class="text-xs-right">{{ props.item.contractNo }}</td>
      <td class="text-xs-right">{{ props.item.contractAmt }}</td>
      <td class="text-xs-right">{{ props.item.maturityAmt}}</td>
      <td class="text-xs-right">{{ props.item.payoutAmtTD}}</td>
      <td class="text-xs-right">{{ props.item.balance}}</td>
      <td class="text-xs-right">{{ props.item.maturityDate | moment("DD-MMM-YY") }}</td>
      <td class="text-xs-right">{{ props.item.status }}</td>
    </template>
  </v-data-table>
</template>

<script>

  function format2(n, currency) {
      return currency + " " + n.toFixed(2).replace(/(\d)(?=(\d{3})+\.)/g, "$1,");
  }

  export default {
    name:'DataTable',
    data () {
      return {
        headers: [
          {
            text: 'Contract Details',
            align: 'center',
            sortable: true,
            value: 'name'
          },
          { text: 'Contract No', value: 'contractNo' },
          { text: 'Contract Amt', value: 'Contract Amount' },
          { text: 'Maturity Amt', value: 'Maturity Amount' },
          { text: 'Payout Amt ToDate', value: 'Maturity Amount' },
          { text: 'Balance', value: 'Maturity Amount' },
          { text: 'Maturity Date', value: 'Maturity Date' },
          { text: 'Status', value: 'Status' }
        ],
        items: [
          {
            value: false,
            name: 'Titanium 60 Series 2',
            contractNo: '200000012',
            contractAmt: format2(6000, "$"),
            maturityAmt: format2(7500, "$"),
            payoutAmtTD: format2(4000, "$"),
            balance: format2(3500, "$"),
            maturityDate: new Date('4/23/2018'),
            status: 'Active'
          }
        ]
      }
    }
  }
</script>