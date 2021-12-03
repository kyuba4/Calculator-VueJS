<template>
   <div>
      <h1>Calculator</h1>
      <div class="wrap">
         <div class="display">
            <div class="result">
               <span class="result__number">{{ result }}</span>
               <span class="result__action">{{ action }}</span>
            </div>
            <div class="current-number">
               <span>{{ currentNumber }}</span>
            </div>
         </div>
         <div class="buttons">
            <Button v-for="(button, index) in buttons" :key="index" :buttonType="button" v-html="button" />
         </div>
      </div>
   </div>
</template>

<script>
import Button from "@/components/Button.vue";

export default {
   name: "Home",
   components: {
      Button,
   },
   data() {
      return {
         result: 30,
         action: "+",
         currentNumber: 15,
         buttons: [
            "%",
            "CE",
            "C",
            "Delete",
            "1/x",
            "x&#178;",
            "√",
            "÷",
            "7",
            "8",
            "9",
            "×",
            "4",
            "5",
            "6",
            "-",
            "1",
            "2",
            "3",
            "+",
            "±",
            "0",
            ",",
            "=",
         ],
      };
   },
   methods: {},
};
</script> 

<style lang="scss" scoped>
h1 {
   font-weight: 500;
   font-size: 3rem;
   text-align: center;
}

.wrap {
   height: 600px;
   width: 400px;
   border: 2px solid #5c5c5c;
   position: absolute;
   top: 50%;
   left: 50%;
   transform: translate(-50%, -50%);
   border-radius: 15px;
   box-shadow: 0 0 5px 0 #00000086;
   overflow: hidden;

   .display {
      width: 100%;
      height: 110px;
      border-radius: 15px 15px 0 0;
      display: flex;
      flex-direction: column;

      .result,
      .current-number {
         height: 50%;
         font-size: 1.5rem;
         display: flex;
         align-items: center;
         justify-content: flex-end;
         width: 95%;
         margin: 0 auto;
      }

      .result {
         color: grey;

         &__action {
            margin-left: 5px;
         }
      }

      .current-number {
         span {
            font-size: 2.1rem;
         }
      }
   }

   //  .buttons {
   //  }
}
</style>
