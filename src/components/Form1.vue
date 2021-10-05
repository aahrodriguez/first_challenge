<template>
    <v-card outlined>
        <v-container>
            <v-form>
                <div>Please enter a few details about your client</div>
                <div class="mt-5">
                    <v-autocomplete
                        v-model="occupation"
                        :items="occupation_items"
                        outlined
                        label="Occupation"
                    ></v-autocomplete>
                </div>
                <div>
                    <v-autocomplete
                        v-model="states"
                        :items="states_items"
                        outlined
                        label="States"
                        hint="Coverage exlusive to Australian companies"
                        persistent-hint
                    ></v-autocomplete>
                </div>
                <div class="mt-5">
                    <v-text-field
                        v-model="amount"
                        label="Amount"
                        prefix="AUD"
                        outlined
                        type="number"
                        hint="Up to 50M maximum annual revenues"
                        persistent-hint
                        :append-icon="!amount || amount > 50000000 || amount <= 0 ? 'mdi-alert-circle-outline' : 'mdi-check'"
                        :rules="amountRules"
                    ></v-text-field>
                </div>
                <div class="mt-5">
                    <v-text-field
                        v-model="employees"
                        label="Number of employees"
                        outlined
                        type="number"
                        hint="Up to 100 maximum numbers of employees"
                        persistent-hint
                        :rules="employeesRules"
                        :append-icon="employees > 100 || employees <= 0  ? 'mdi-alert-circle-outline' : 'mdi-check'"
                    ></v-text-field>
                </div>

                <div class="text-center">
                    <v-btn
                        color="primary"
                        class="mt-5"
                        large
                        depressed
                        :disabled="isDisabled"
                    >
                        Next
                    </v-btn>
                </div>
            </v-form>
        </v-container>
    </v-card>
</template>

<script>
    export default {
        data: () => ({
            occupation: '',
            states: '',
            amount: 0,
            employees: 0,
            
            occupation_items: ["Accountant", "Lawyer", "Engineer", "Nutrition", ""], 
            states_items: ["New South Wales", "Victoria", "Queensland", "Tasmania", "South Australia", "Western Australia", "Northern Territory", "Australian Capital Territory"],


            employeesRules: [
               function( v ) {
                  if( !( v <= 100) ){
                    return  'Up to 100 maximum numbers of employees'
                  }
                }
            ],
            amountRules: [
               function( v ) {
                  if( !( v <= 50000000) ){
                    return  'Up to 50 M maximum annual revenues'
                  }
                },
            ]
        }),
        computed: {
            isDisabled: function(){
                return (
                    !this.occupation ||
                    !this.states ||
                    !this.amount ||
                    !this.employees ||
                    this.amount > 50000000 ||
                    this.employees > 100
                )
            }
        }
    }
</script>

