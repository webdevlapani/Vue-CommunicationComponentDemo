<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>{{myName}}</p> <!-- Output of props -->
        <p>My Name is : {{switchName()}}</p>
        <p>User age is : {{userAge}}</p>
        <button @click="resetName">Reset Name</button>
        <button @click="resetNameUsingProps">Reset Name Using Props</button>  <!--call parent resetNameUsingProps function using props-->
    </div>
</template>

<script>
    import {eventBus} from "../main";

    export default {
      /*
      * props: ['myName',] // Simple way to pass props
      *
      * props: {
            myName: [String, Number] // We can also provide type of props
        }
      *
      * props: {
      *     myName : {
      *         type: String, // string type of props
      *         default: 'Shiva', // We can also provide default value of props
      *         required: true // we need to pass this props compulsory
      *     }
      * }
      *
      * */
      props: {
        myName: String,
        resetNameUsingProps: Function, // call parent resetNameUsingProps function from child
        userAge: Number
      },
      methods:{
        switchName: function () {
          return this.myName.split('').reverse().join(''); // We can also access props value like this
        },
        resetName: function () {
            this.myName = 'Shiva';
            this.$emit('nameWasReset', this.myName) // emit nameWasReset event to parent component and pass data to parent component
        }
      },
      created() {
        eventBus.$on('ageWasEdited', (data) => this.userAge = data)
      }
    }
</script>

<style scoped> /*scoped use for provide style for particular component  */
    div {
        background-color: lightcoral;
    }
</style>
