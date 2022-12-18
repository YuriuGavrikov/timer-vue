<script setup>
import { ref } from "vue";
import Timer from "./Timer.vue";

const userDb = [
   {
      id: 1,
      name: "Участник 1",
      availabilityEvents: "-",
      productionTime: "80",
      guarantees: 24,
      paymentTerms: "30%",
      manufacturingCost: "3,700,000 руб",
      actions: "-",
   },
   {
      id: 2,
      name: "Участник 2",
      availabilityEvents: "-",
      productionTime: "90",
      guarantees: 24,
      paymentTerms: "100%",
      manufacturingCost: "2,700,000 руб",
      actions: "-",
   },
   {
      id: 3,
      name: "Участник 3",
      availabilityEvents: "-",
      productionTime: "75",
      guarantees: 22,
      paymentTerms: "60%",
      manufacturingCost: "3,200,000 руб",
      actions: "-",
   },
   {
      id: 4,
      name: "Участник 4",
      availabilityEvents: "-",
      productionTime: "60",
      guarantees: 28,
      paymentTerms: "10%",
      manufacturingCost: "4,700,000 руб",
      actions: "-",
   },
];

let timerPosition = ref(1);
const timerPositionChenge = () => {
   if (timerPosition.value < userDb.length) {
      timerPosition.value++;
   } else {
      timerPosition.value = 1;
   }
};
</script>

<template>
   <table class="table table-striped-columns">
      <tbody class="tbody">
         <tr>
            <td>ХОД</td>
            <td>Параметры и требования</td>
            <td>
               Наличие комплекса мероприятий, повышающих стандарты качества
               изготовления
            </td>
            <td>Срок изготовления лота, дней</td>
            <td>Гарантийные обязатольства, мес</td>
            <td>Условия оплаты</td>
            <td>Стоимост изготовления лота, руб.(без НДС)</td>
            <td>Действия</td>
         </tr>
         <tr class="user_tr" v-for="user in userDb" :key="user.id">
            <td>
               <div v-if="user.id === timerPosition">
                  <Timer @onTimerPositionChenge="timerPositionChenge" />
               </div>
            </td>
            <td>{{ user.name }}</td>
            <td>{{ user.availabilityEvents }}</td>
            <td>{{ user.productionTime }}</td>
            <td>{{ user.guarantees }}</td>
            <td>{{ user.paymentTerms }}</td>
            <td>{{ user.manufacturingCost }}</td>
            <td>{{ user.actions }}</td>
         </tr>
      </tbody>
   </table>
</template>

<style scoped>
.tbody {
   display: flex;
}
.user_tr {
   text-align: center;
}
.tbody tr {
   display: flex;
   flex-direction: column;
   flex-wrap: wrap;
   width: 100%;
}
.tbody td {
   height: 50px;
   font-size: 12px;
}
</style>
