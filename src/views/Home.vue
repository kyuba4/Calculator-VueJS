<template>
   <div>
      <h1>Calculator <span>VueJS</span></h1>
      <div class="wrap">
         <div class="display">
            <div class="result">
               <span class="result__number">{{ result ? Math.round(result * 10000000) / 10000000 : null }}</span>
               <span class="result__action" v-show="action">{{ action }}</span>
            </div>
            <div class="current-number">
               <span>{{ Math.round(currentNumber * 10000000) / 10000000 }}</span>
            </div>
         </div>
         <div class="buttons">
            <Button v-for="(button, index) in buttons" :key="index" :buttonType="button" v-html="button" @click="click" />
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
         result: null,
         action: "",
         currentNumber: "",
         buttons: [
            "%",
            "CE",
            "C",
            "Delete",
            "1/x",
            "x&#178;",
            "√",
            "/",
            "7",
            "8",
            "9",
            "*",
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
   methods: {
      actionHandler(action) {
         this.action = action;

         if (this.result != null && this.currentNumber) {
            switch (action) {
               case "+":
                  this.result += parseFloat(this.currentNumber);
                  break;
               case "-":
                  this.result -= parseFloat(this.currentNumber);
                  break;
               case "*":
                  this.result *= parseFloat(this.currentNumber);
                  break;
               case "/":
                  this.result /= parseFloat(this.currentNumber);
                  break;
            }
         } else if (this.result == null) {
            this.result = parseFloat(this.currentNumber);
            this.action = action;
         } else if (!this.currentNumber) {
            this.action = action;
         }
         this.currentNumber = "";
      },
      clearEntry() {
         this.currentNumber = "";
      },
      clear() {
         this.currentNumber = "";
         this.action = "";
         this.result = null;
      },
      equal() {
         this.action = "";
         this.currentNumber = this.result.toString();
         this.result = null;
      },
      delete() {
         this.currentNumber = this.currentNumber.substring(0, this.currentNumber.length - 1);
      },
      changeToOpposite() {
         this.currentNumber *= -1;
      },
      exponentiation() {
         this.currentNumber *= this.currentNumber;
      },
      root() {
         this.currentNumber = Math.sqrt(this.currentNumber);
      },
      percentage() {
         if (this.result && this.currentNumber) {
            if (this.action == "*") {
               this.currentNumber = (this.result * parseFloat(this.currentNumber)) / 100;
            } else if (this.action == "+") {
               this.currentNumber = (this.result * parseFloat(this.currentNumber)) / 100 + this.result;
            } else if (this.action == "-") {
               this.currentNumber = this.result - (this.result * parseFloat(this.currentNumber)) / 100;
            }
         } else {
            return;
         }

         this.currentNumber = this.currentNumber.toString();
         this.result = null;
         this.action = "";
      },
      adversity() {
         this.currentNumber = 1 / this.currentNumber;
      },
      comma() {
         if (!this.currentNumber.includes(".")) {
            this.currentNumber = this.currentNumber + ".";
         }
      },
      click(type) {
         if (!isNaN(type)) {
            this.currentNumber += type;
         } else {
            switch (type) {
               case "+":
                  this.actionHandler("+");
                  break;
               case "-":
                  this.actionHandler("-");
                  break;
               case "*":
                  this.actionHandler("*");
                  break;
               case "/":
                  this.actionHandler("/");
                  break;
               case "=":
                  this.actionHandler(this.action);
                  this.equal();
                  break;
               case "√":
                  this.root();
                  break;
               case "%":
                  this.percentage();
                  break;
               case "CE":
                  this.clearEntry();
                  break;
               case "C":
                  this.clear();
                  break;
               case "Delete":
                  this.delete();
                  break;
               case "1/x":
                  this.adversity();
                  break;
               case "±":
                  this.changeToOpposite();
                  break;
               case "x&#178;":
                  this.exponentiation();
                  break;
               case ",":
                  this.comma();
                  break;
            }
         }
      },
   },
};
</script> 

<style lang="scss" scoped>
h1 {
   font-weight: 500;
   font-size: 3rem;
   text-align: center;
   color: #35495e;
   span {
      color: #42b883;
   }
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
   background: #ffffff10;

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
            font-size: 2.5rem;
         }
      }
   }

   //  .buttons {
   //  }
}
</style>
