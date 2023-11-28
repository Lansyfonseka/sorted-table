<script setup>
import './Table.scss';

const props = defineProps({
  databaseOfClients: Array
});

const emits = defineEmits(['sortID']);
console.log(props.databaseOfClients);

</script>

<template>
  <div class="table">
    <div class="table-row table-header">
      <div @click="$emit('sortID')">№ Клиента</div>
      <div>Имя</div>
      <div>Диета</div>
      <div>Тариф</div>
      <div>Адрес</div>
      <div>Телефон</div>
      <div>Даты</div>
      <div>Скидка</div>
      <div>Оплата</div>
      <div>Комментарий курьера</div>
      <div>Комментарий внутренний</div>
      <div>Статус</div>
    </div>
    <div v-for="client in databaseOfClients" class="table-row">
      <div>{{ client.o_id }}</div>
      <div>{{ client.client_name }}</div>
      <div class="table-row--listItem table-row--listItemDotted">
        <div v-for="diet in client.diets">{{ diet }}</div>
      </div>
      <div class="table-row--listItem table-row--listItemDotted itemCenter">
        <div v-for="tarif in client.tariff">{{ tarif }}</div>
      </div>
      <div>{{ client.address }}</div>
      <div>{{ client.phone }}</div>
      <div class="table-row--listItem table-row--listItemDotted itemCenter">
        <div v-for="date in client.dates">{{ date.start_date.toLocaleDateString() }} - {{ date.end_date.toLocaleDateString() }}</div>
      </div>
      <div class="itemCenter">{{ client.discount }}</div>
      <div class="table-row--listItem">
        <div>Стоим:{{ client.order_sum }}</div>
        <div>{{ client.pay_status }}</div>
        <div>Долг:{{ client.order_sum - client.order_payed }}</div>
      </div>
      <div>{{ client.courier_comment }}</div>
      <div>{{ client.inner_comment }}</div>
      <div class="table-row--listItem table-row--listItemDotted">
        <div v-for="timeStatus in client.status">
          {{ 
            timeStatus.done ? `Завершилось ${timeStatus.days} дней назад` : 
            timeStatus.days < 0 ? `Завершиться через ${-timeStatus.days} дней` : 
            `Начнется через ${timeStatus.days} дней`
          }}
        </div>
      </div>
    </div>
  </div>
</template>
