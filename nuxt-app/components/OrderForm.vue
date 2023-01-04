<template>
  <form @submit.prevent="handleSubmit()" class="order-form">
    <input
      class="order-form-name"
      required
      type="text"
      placeholder="Введите свое имя*"
    />
    <input
      class="order-form-number"
      required
      type="text"
      placeholder="Укажите свой телефон*"
    />
    <textarea
      cols="30"
      rows="10"
      placeholder="Напишите, что вас интересует ( не обязательно )"
    ></textarea>
    <span>
      Нажимая на кнопку отправки, вы даете согласие на обработку своих
      персональных данных
    </span>
    <UIButton class="order-button" type="submit"> {{btnText}} </UIButton>
  </form>
</template>

<script setup>
const props = defineProps({
  btnText: String
})
const emit = defineEmits(["onSubmit"]);

const handleSubmit = () => {
    emit('onSubmit')
}
</script>

<style scoped>
.order-form {
  display: flex;
  flex-direction: column;
  margin-top: 2rem;
}
.order-form * {
  margin-bottom: 0.7rem;
}
.order-button {
  align-self: flex-start;
}
</style>
