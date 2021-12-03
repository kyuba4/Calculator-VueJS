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
   width: calc(396px / 4);
   height: calc((596px - 110px) / 6);
   font-size: 1.2rem;
   cursor: pointer;
   transition: 50ms;

   &:hover {
      background: #c7d4f069;
   }
}
</style>