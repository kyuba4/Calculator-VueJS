<template>
   <button @click="$emit('click', buttonType)">
      {{ buttonType }}
   </button>
</template>
<script>
export default {
   name: "Button",
   props: ["buttonType"],
};
</script>
<style lang="scss" scoped>
button {
   border: 0;
   outline: 0;
   background: transparent;
   width: calc(380px / 4);
   height: calc((572px - 110px) / 6);
   font-size: 1.2rem;
   cursor: pointer;
   transition: 100ms linear;
   margin: 2px;

   &:hover {
      background: #b4c3e269;
   }
}
</style>