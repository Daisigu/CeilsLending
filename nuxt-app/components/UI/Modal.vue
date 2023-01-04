<template>
  <transition name="fade">
    <div class="modal-backdrop" v-show="open" @click.self="close()">
      <div class="modal-content">
        <div :class="{ 'vue-modal-main': !imageModal }">
          <div class="modal-header" v-if="!imageModal">
            <div>
              <slot name="header" />
            </div>
            <span @click="close">
              <span class="close-modal-button"><i class="bi bi-x-lg"></i></span>
            </span>
          </div>
          <div class="modal-body">
            <slot name="main" />
          </div>
          <div class="modal-footer" v-if="!imageModal">
            <slot name="footer" />
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
const props = defineProps({
  open: Boolean,
  imageModal: Boolean,
});
const emit = defineEmits(["close"]);
const close = () => {
  emit("close");
};
const handleKeyUp = (event) => {
  event.keyCode === 27 ? close() : 0;
};
onMounted(() => document.addEventListener("keyup", handleKeyUp));
onUnmounted(() => document.removeEventListener("keyup", handleKeyUp));
</script>

<style scoped>
.modal-backdrop {
  display: flex;
  justify-content: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  background-color: rgba(0, 0, 0, 0.58);
  z-index: 1;
}
.close-modal-button{
  cursor: pointer;
}
.modal-content {
  max-width: 500px;
  margin: 5rem 1rem;
  height: fit-content;
}
.modal-footer {
  display: flex;
  justify-content: flex-end;
}
.modal-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  border-bottom: 1px solid lightgray;
}
.vue-modal-main {
  position: relative;
  background-color: #fff;
  border: 1px solid rgba(0, 0, 0, 0.113);
  background-clip: padding-box;
  border-radius: 0.3rem;
  padding: 1rem;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
