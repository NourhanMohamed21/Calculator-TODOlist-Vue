<template>
  <div class="container-fluid  Display">
    <b-container class="bv-example-row mb-3 ">
      <b-row cols="4">
        <b-col cols="12" class="Display org2">{{ current || 0 }}</b-col>
        <b-col @click="ACFun" class="FirstR org btn">AC</b-col>
        <b-col @click="posNeg" class="FirstR org"> +/-</b-col>
        <b-col @click="perct" class="FirstR org">%</b-col>
        <b-col @click="divide" class="operator org">/</b-col>
        <b-col @click="Append('7')" class="Numbers org">7</b-col>
        <b-col @click="Append('8')" class="Numbers org">8</b-col>
        <b-col @click="Append('9')" class="Numbers org">9</b-col>
        <b-col @click="Times" class="operator org">X</b-col>
        <b-col @click="Append('4')" class="Numbers org">4</b-col>
        <b-col @click="Append('5')" class="Numbers org">5</b-col>
        <b-col @click="Append('6')" class="Numbers org">6</b-col>
        <b-col @click="Minus" class="operator org">-</b-col>
        <b-col @click="Append('1')" class="Numbers org">1</b-col>
        <b-col @click="Append('2')" class="Numbers org">2</b-col>
        <b-col @click="Append('3')" class="Numbers org">3</b-col>
        <b-col @click="Add" class="operator org">+</b-col>
        <b-col cols="6" @click="Append('0')" class="Numbers org">0</b-col>
        <b-col @click="dot" class="Numbers org dot">.</b-col>
        <b-col @click="out" class="operator org">=</b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
export default {
  name: "Calculator",
  data() {
    return {
      current: "",
      previousVal: "",
      operator: false,
      operation: null,
    };
  },
  methods: {
    ACFun() {
      this.current = "";
    },
    Append(number) {
      if (!this.operator) this.current = this.current + number;
      else {
        this.previousVal = this.current;
        this.current = number;
        this.operator = false;
      }
    },
    posNeg() {
      if (this.current[0] === "-")
        this.current = this.current.slice(1, this.current.length);
      else this.current = "-" + this.current;
    },
    perct() {
      this.current = this.current / 100;
    },
    dot() {
      if (this.operator) {
        this.previousVal = this.current;
        this.current = "0.";
        this.operator = false;
      }
      if (!this.current.includes(".")) this.current = this.current + ".";
    },
    setPrev() {
      this.previousVal = this.current;
      this.operator = true;
    },
    Add() {
      this.operation = (a, b) => a + b;
      this.setPrev();
    },
    Minus() {
      this.operation = (a, b) => a - b;
      this.setPrev();
    },
    divide() {
      this.operation = (a, b) => a / b;
      this.setPrev();
    },
    Times() {
      this.operation = (a, b) => a * b;
      this.setPrev();
    },

    out() {
      this.current = this.operation(
        parseFloat(this.previousVal),
        parseFloat(this.current)
      );
      this.previousVal = 0;
    },
  },
};
</script>

<style scoped>
.operator {
  /* border-radius: 20%; */
  background-color: var(--operator-color);
  /* padding: 2%; */
  color: var(--white);
}
.org {
  padding: 2%;
  border: white;
  border: 2px;
  border-style: solid;
  font-size: var(--default-font-size);
     cursor: pointer;
}
.org2 {
    background-color: black;
  padding: 2%;
  border: white;
  border: 2px;
  border-style: solid;
  font-size: var(--default-font-size);
}
.Numbers {
  background-color: var(--Numbers-color);
  /* padding: 2%; */
  color: var(--white);
}
.dot {
  font-size: 20pt;
}
.FirstR {
  background-color: var(--firstR-color);
  color: var(--white);
}
.Display {
  /* background-color: black; */
  color: white;
  font-size: var(--default-font-size);
  padding-top: 1.5%;
  
}


</style>

