<script setup>
import Header from "./components/ExpenseTracker/Header.vue"
import Balance from "./components/ExpenseTracker/Balance.vue"
import IncomeExpenses from "./components/ExpenseTracker/IncomeExpenses.vue"
import TransactionList from "./components/ExpenseTracker/TransactionList.vue"
import AddTransaction from "./components/ExpenseTracker/AddTransaction.vue"

import { computed, ref } from "vue";
const transactions = ref([
  { id: 1, text: "Flower", amount: -19.99 },
  { id: 1, text: "Salary", amount: 299.97 },
  { id: 1, text: "Book", amount: -10 },
  { id: 1, text: "Camera", amount: 150 },
]);
// get total
const total = computed(()=>{
  return transactions.value.reduce((acc,transaction)=>{
    return acc+transaction.amount
  },0)
})

//get income

const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0)
    .toFixed(2);
});


//get expense 

const expense = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0)
    .toFixed(2);
});

// Add Transaction 
const handleTransactionSubmitted = (transactionData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionData.text,
    amount: transactionData.amount,
  });

  saveTransactionsToLocalStorage();

  toast.success('Transaction added.');
};

// Generate unique ID
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};
</script>

<template>
  <Header/>
  <div class="container">
    <Balance :total="+total"/>
    <IncomeExpenses :income="+income" :expense="+expense"/>
    <TransactionList :transactions="transactions"/>
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted"/>
  </div>
</template>

<style scoped>

</style>
