<template>
  <v-container fluid grid-list-md>
    <v-layout row wrap>
      <v-flex d-flex xs12 sm6 md4>
         <v-card color="indigo darken-4" dark>
           <div>
             <div class="headline">{{InvestorName}}</div>
           </div>
           <v-card-title primary class="title">Investor: {{investorName}}</v-card-title>
           <v-card-text>
             <v-flex d-flex xs12>
               <v-flex d-flex xs4>
                 <div>
                   <h5>Address</h5>
                   <span>{{blk}} </span><span class="text-xs-left">{{street}}</span> <br>
                   <span>{{unit}}</span> <span>{{bldg}}</span> <br>
                   <span>{{country}}</span> <span>{{postcode}}</span>
                 </div>
             </v-flex>
             <v-flex d-flex xs4>
               <div>
                 <h5>Contacts</h5>
                 <span>{{email}}</span> <br>
                 <span>{{mobile}}</span>
               </div>
             </v-flex>
             <v-flex d-flex xs4>
           
               <img class="image" :src="`https:randomuser.me/api/portraits/women/${8}.jpg`" 
                    alt="lorem" width="100%" height="100%">
              
             </v-flex>
           </v-flex>
           </v-card-text>
         </v-card>
       </v-flex>
       <v-flex d-flex xs12 sm6 md3>
         <v-layout row wrap>
           <v-flex d-flex>
             <v-card color="indigo" dark>
               <v-card-text
               v-text="lorem.slice(0, 70)">
               </v-card-text>
             </v-card>
           </v-flex>
           <v-flex d-flex>
             <v-layout row wrap>
               <v-flex d-flex v-for="n in 2"
                 :key="n"
                 xs12
               >
                 <v-card
                   color="red lighten-2"
                   dark
                 >
                   <v-card-text
                   v-text="lorem.slice(0, 40)">
                   </v-card-text>
                 </v-card>
               </v-flex>
             </v-layout>
           </v-flex>
         </v-layout>
       </v-flex>
       <v-flex d-flex xs12 sm6 md2 child-flex>
         <v-card color="green lighten-2" dark>
           <v-card-text
           v-text="lorem.slice(0, 90)">
           </v-card-text>
         </v-card>
       </v-flex>
       <v-flex d-flex xs12 sm6 md3>
         <v-card color="blue lighten-2" dark>
           <v-card-text
           v-text="lorem.slice(0, 100)">
           </v-card-text>
         </v-card>
       </v-flex>
     </v-layout>
   </v-container>
 </template>


<script>
  export default {
    data () {
      return {
        investorName: 'Lara Croft',
        blk: '1',
        street: 'Desert Road',
        unit: '#B1-01',
        bldg: 'The Pyramid',
        country: 'Egypt',
        postcode: '1007900',
        email: 'lara.croft@tombraider.com',
        mobile: '+13-9234-5678',
        card_text: 'Lorem ipsum dolor sit amet, brute iriure accusata ne mea. Eos suavitate referrentur ad, te duo agam libris qualisque, utroque quaestio accommodare no qui. Et percipit laboramus usu, no invidunt verterem nominati mel. Dolorem ancillae an mei, ut putant invenire splendide mel, ea nec propriae adipisci. Ignota salutandi accusamus in sed, et per malis fuisset, qui id ludus appareat.',
        lorem: `Lorem ipsum dolor sit amet, mel at clita quando. Te sit oratio vituperatoribus, nam ad ipsum posidonium mediocritatem, explicari dissentiunt cu mea. Repudiare disputationi vim in, mollis iriure nec cu, alienum argumentum ius ad. Pri eu justo aeque torquatos.`
      }
    }
  }
</script>