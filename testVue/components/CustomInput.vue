<template>
  <input 
    type="text"
    :value="dValue"
    @blur="blurEvent()"

  >
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from "vue-property-decorator";

@Component
export default class CustomInput extends Vue {
  @Prop({ default: ''})public pValue!: string;
  public dValue: string = this.pValue;
  @Watch('pValue', {immediate: true})
  changeValue(v:string) {
    this.dValue = v;
  }

  public blurEvent() {

  }
}
</script>
