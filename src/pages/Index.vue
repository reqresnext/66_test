<template>
  <q-page class="flex">
    <div v-if="!letterColumn.length" class="column justify-center">
        <div class="row justify-center text-h6 text-weight-bold text-indigo q-pa-lg text-center">
          Для начала работы пожалуйста введите любой буквенный символ на клавиатуре
        </div>
    </div>
   
    <transition-group name="fade" tag="div" v-else class="column">
      
      <div class="row justify-center text-h2 text-weight-bold text-teal items-center" v-for="(letter, index) in letterColumn" :key="letter + index">{{ letter }}</div>
    
    </transition-group>
  </q-page>

    
      
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      letterColumn: []
    }
  },
  methods: {
    checkIfChar(char) {
      return char.toLowerCase() != char.toUpperCase();
    }
  },
   mounted() {
	window.addEventListener("keypress", e => {
    console.log(e.key);
    console.log()
    if(this.checkIfChar(e.key)) {
      this.letterColumn.push(e.key)
    } else {
      return;
    }
    
	});
}
}
</script>

<style lang="scss">
  .column {
    width: 100%;
    line-height: 10px;
  }
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 3s;
  }

  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }

    
</style>
