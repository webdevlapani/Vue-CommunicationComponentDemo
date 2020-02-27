<template>
    <div class="component">
        <h1>The User Component</h1>
        <p>I'm an awesome User!</p>
        <button @click="changeMyName">Change My Name</button>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6">
                <app-user-detail
                        :myName="name"
                        @nameWasReset="resetName"
                        :resetNameUsingProps="resetNameUsingProps"
                        :userAge="age">
                </app-user-detail>
            </div>
            <div class="col-xs-12 col-sm-6">
                <app-user-edit :userAge="age" @ageWasEdited="age = $event"></app-user-edit>
            </div>
        </div>
        <p>My Name Is : {{name}}</p>

    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {
        data: function() {
          return {
            name: 'Shiva',
            age: 27
          }
        },
        methods: {
          changeMyName: function () {
            this.name = 'Mahadev';
          },
          resetName: function (event) {
            this.name = event;
          },
          /*
          * this function is pass using props parents to child
          * */
          resetNameUsingProps: function () {
            this.name = 'Shiva';
          }
        },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        }
    }
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
