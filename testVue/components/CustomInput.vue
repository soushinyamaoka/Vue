<template>
  <input 
    type="text"
    :value="dValue"
    @input="$emit('input', $event.target.value)" 
    @blur="blurEvent()"

  >
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from "vue-property-decorator";

@Component
export default class CustomInput extends Vue {
  @Prop({ default: ''})public pValue!: any;
  public dValue: string = this.pValue;

  @Watch('pValue', {immediate: true})
  changeValue(v: any) {
    this.dValue = v;
  }

  public blurEvent() {

  }
}
</script>
