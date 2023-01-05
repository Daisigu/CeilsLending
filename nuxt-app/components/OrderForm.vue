<template>
  <form @submit.prevent="handleSubmit()" class="order-form">
    <input
      class="order-form-name"
      required
      v-model.trim="formSubmitData.name"
      type="text"
      placeholder="Введите свое имя*"
      maxlength="50"
    />
    <input
      class="order-form-number"
      required
      v-model.trim="formSubmitData.phone"
      maxlength="50"
      type="text"
      placeholder="Укажите свой телефон*"
    />
    <textarea
      cols="30"
      v-model.trim="formSubmitData.comment"
      rows="10"
      maxlength="550"
      placeholder="Напишите, что вас интересует ( не обязательно )"
    ></textarea>
    <span>
      Нажимая на кнопку отправки, вы даете согласие на обработку своих
      персональных данных
    </span>
    <UIButton class="order-button" type="submit"> {{ btnText }} </UIButton>
  </form>
</template>

<script setup>
const props = defineProps({
  btnText: String,
});
const emit = defineEmits(["onSubmit"]);
const formSubmitData = ref({
  name: "",
  phone: "",
  comment: "",
});

const handleSubmit = () => {
  emit("onSubmit", formSubmitData);
};
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
