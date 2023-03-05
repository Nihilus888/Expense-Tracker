<template>
  <HeaderExpense :totalExpense="state.totalExpense"/>
</template>

<script>
import { reactive, computed } from "vue";
import HeaderExpense from "./components/HeaderExpense.vue";

export default {
    setup() {
        const state = reactive({
            expense: [{
                value: 400
            },
            {
                value: 500
            },
            {
                value: 100
            }
            ],
            totalExpense: computed(() => {
                let temp = 0;
                if (state.expense.length > 0) {
                    for (let i = 0; i < state.expense.length; i++) {
                        temp += state.expense[i].value;
                    }
                }
                return temp;
            }),
        });
        return {
            HeaderExpense,
            state,
        };
    },
    components: { HeaderExpense }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}

body {
  background: #eee;
}
</style>
