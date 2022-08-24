<script setup lang="ts">
// import { reactive } from 'vue';

/*_________________typescript____________*/

// this can solve both 1st and 2nd problem
enum Gender {
  GIRL = 'girl',
  UNISEX = 'unisex',
  BOY = 'boy',
}
enum Popularity {
  TRENDY = 'trendy',
  UNIQUE = 'unique',
}
enum Length {
  SHORT = 'short',
  ALL = 'all',
  LONG = 'long'
}

interface OptionsState {
  gender:Gender,
  popularity:Popularity,
  length: Length,
}


// this can solve 1st problem
// interface OptionsState {
//   gender:string,
//   popularity:string,
//   length:string
// }

/*_______________main object_________________*/
/*
  here we have 2 problem:
  1)value of gender, popularity ... can be anything like Num and other Strings
  2)we can write another Key:Value and nothing will be wrong, but its actually wrong
  TypeScript can help us with (interface && enum)
*/
  const options = reactive<OptionsState>({
    // const options: OptionsState = reactive({
    gender:Gender.BOY,
    popularity:Popularity.UNIQUE,
    length:Length.ALL,
  })

</script>

<template>
  <div style="display:flex;flex-direction:column;align-items:center">
    <h1>
      baby name generator
    </h1>
    <p>
      choose opiton and click the "Find Name" button
    </p>

    <div class="options-container">
      <div class="option-container">
      <h4>choose gender</h4>
        <div class="option-btns">
          <button :class="{ active: options.gender == 'boy' }">Boy</button>
          <button :class="{ active: options.gender == 'unisex' }">Unisex</button>
          <button :class="{ active: options.gender == 'girl' }">Girl</button>
        </div>
      </div>
      <div class="option-container">
      <h4>choose the name popularity</h4>
        <div class="option-btns">
          <button :class="{ active: options.popularity == 'trendy' }">Trendy</button>
          <button :class="{ active: options.popularity == 'unique' }">Unique</button>
        </div>
      </div>
      <div class="option-container">
      <h4>choose the name's length</h4>
        <div class="option-btns">
          <button :class="{ active: options.length == 'long' }">Long</button>
          <button :class="{ active: options.length == 'all' }">All</button>
          <button :class="{ active: options.length == 'short' }">Short</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style>

  .active{
    background-color: red;
  }
</style>


