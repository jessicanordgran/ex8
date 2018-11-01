<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Directives Exercise</h1>
                <!-- Exercise -->
                <!-- Build a Custom Directive which works like v-on (Listen for Events) -->
            <button v-customOn:click="clicked" class="btn btn-primary">Click</button>
            </div>
        </div>
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Filters & Mixins</h1>
                <!-- Exercise 1) -->
                <!-- Build a local Filter which reverses the Text it is applied on -->
                <p>{{someText | reverse}}</p>


                <!-- Exercise 2 -->
                <!-- Build a global Filter which counts the length of a word and it appends it -->
                <!-- Like this: "Test" => Gets Filtered to => "Test (4)" -->

                <p>{{secondText | calculateLength}}</p>

                <!-- Exercise 3 -->
                <!-- Do the same as in Exercises 1 & 2, now with Computed Properties -->
                <p>{{reverse}}</p>
                <p>{{lengthAware}}</p>

                <!-- Exercise 4 -->
                <!-- Share the Computed Property rebuilding Exercise 2 via a Mixin -->
            </div>
        </div>
    </div>
</template>

<script>
    import {lengthAware} from "./lengthAware.js";

    export default {
        data(){
            return{
                someText: 'here is some text',
                secondText: 'second text area'
            }
        },
        mixins:[lengthAware],
        filters:
            {
                reverse(value){
                    return value.split("").reverse().join("");
                }
            },
        directives: {
            customOn:{
                bind(el, binding){
                    const type = binding.arg;
                    const fn = binding.value;

                    el.addEventListener(type, fn);
                }
            }
        },
        methods: {
            clicked(){
                alert('was clicked');
            }
        },
        computed:{
            revere(){
                return this.someText.split("").reverse().join("");
            }

        }
    }
</script>

<style>
</style>
