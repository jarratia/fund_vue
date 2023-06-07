<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter}} </p>

  <div>
    <button class="btn primary" v-on:click="increase">+1</button>
    <button class="btn warning" v-on:click="decrease">-1</button>
  </div>
</template>

<script>
export default {
    name: 'Counter',
    props: {
        title: String,
        start: {
            type: Number,
            required: true,
            default: 100,
            //validator
            validator(value) {
                return value > 100
            }
        }
    },

    data() {
        return {
            counter: this.start
        }
    },
    methods: {
        getSquareValue() {
            return this.counter * this.counter
        },

        //Increase
        increase () {
           this.counter++
        },

        //Decrease
        decrease () {
            this.counter--
        }
    },
    computed: {
        // Las propieades computadas se guardan en cache
        squareCounter(){
            return this.counter * this.counter
        },

        //custom title
        customTitle() {
            return this.title || 'Contador'
        }
    }
}
</script>

<style>
    .btn {
        border-radius: 1rem;
        margin: 0 5px;
        width: 100px;
        padding: 30px;
        font-size: 1rem;
    }
    .primary {
        background-color: rgb(77, 77, 231);
        color: rgb(255, 255, 255);
    }

    .warning {
        background-color: rgb(230, 53, 53);
        color: rgb(255, 255, 255);
    }
</style>