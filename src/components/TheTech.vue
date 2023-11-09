<template>
  <div class="tech-wrapper">
    <h1 class="title"> {{ props.name }} </h1>
    <h2 @click="redirect" :class="{ 'card-content': clickable }"> {{ props.value }} </h2>
    <div class="lock">
      <Lock :isLocked="isLocked" />
    </div>
  </div>
</template>

<script setup lang="ts">
import Lock from "@/components/icons/TheLock.vue"
const props = defineProps({
  name: { type: String, required: true },
  isLocked: { type: Boolean, required: true, default: false },
  value: { type: String, required: true, default: '' },
  clickable: { type: Boolean, default: false },
  link: String
})

function redirect() {
  if (props.clickable) {
    window.open(props.link, '_blank', 'noreferrer');
  }
}

</script>

<style scoped>
h2,
h1 {
  width: 100%;
  text-align: center;
  font-size: 18px;
}



.title {
  font-size: 24px;
}

.lock {
  text-align: center;
}


.card:hover {
  cursor: pointer;
  text-decoration: underline;

}

.card-content:hover {
  cursor: pointer;
  text-decoration: underline;
}

.tech-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  margin: 20px;
  width: 250px;
  height: 250px;
  border-radius: 14px;
  box-shadow: rgb(0 0 0 / 29%) 0px 2px 8px 0px
}
</style>