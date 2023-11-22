<script setup>
import database from '../../database/data.json';
import './Table.scss';

console.log(database);
</script>

<template>
  <div class="table">
    <div class="table-row table-header">
      <div>№ Клиента</div>
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
      <div>Срок исполнения</div>
    </div>
    <div v-for="client in database" class="table-row">
      <div>{{ client.o_id }}</div>
      <div>{{ client.client_name }}</div>
      <div>{{ client.diets }}</div>
      <div>{{ client.tariff }}</div>
      <div>{{ client.address }}</div>
      <div>{{ client.phone }}</div>
      <div></div>
      <div>{{ client.discount }}</div>
      <div>{{ client.order_sum }}</div>
      <div>{{ client.courier_comment }}</div>
      <div>{{ client.inner_comment }}</div>
      <div>1</div>
    </div>
  </div>
</template>
