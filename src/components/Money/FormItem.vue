<template>
  <label class="notes">
    <span class="name">{{fieldName}}</span>
    <input type="text"
           :placeholder="placeholderText"
           v-model="value">
  </label>
</template>

<script lang='ts'>
  import Vue from 'vue';
  import {Component, Prop, Watch} from 'vue-property-decorator';

  @Component
  export default class Notes extends Vue {
    value = '';

    @Prop({required:true}) fieldName!: string;
    @Prop({required:true}) placeholderText!: string

    @Watch('value')
    onValueChanged(value: string) {
      this.$emit('update:value', value);
    }
  }
</script>

<style lang='scss' scoped>
  .notes {
    background: #f5f5f5;
    display: block;
    padding: 0 16px;
    display: flex;
    align-items: center;

    .name {
      padding-right: 16px;
    }

    input {
      padding: 16px 0;
      flex-grow: 1;
      background: transparent;
      border: none;
    }
  }
</style>