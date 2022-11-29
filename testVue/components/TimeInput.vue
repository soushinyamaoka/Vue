<template>
  <input 
    type="text"
    :value="dValue"
    @focus="focusEvent()"
    @blur="blurEvent()"
  >
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from "vue-property-decorator";

@Component
export default class TimeInput extends Vue {
  @Prop({ default: ''})public pValue!: string;
  public dValue: string = '';

  @Watch('pValue', {immediate: true})
  changeValue(v: string) {
    this.dValue = v;
  }

  updated() {
    this.$emit("input", this.dValue);
  }

  public focusEvent() {
    this.dValue = this.offColon(this.dValue);
  }

  public blurEvent() {
    this.checkTime(this.dValue);
    this.dValue = this.toColon((this.$el as any).value);
    this.$emit("input", this.dValue);
  }

  private checkTime(value: string) {
    return value.match(/^([01]?[0-9]|2[0-3]):([0-5][0-9])$/) !== null;
  }

  /**************************
 * コロン編集を行うFunction
 **************************/
private toColon(value: string){
  let chgVal: string = value;
  if(value.length == 4){
    var str = value.trim();
    var h = str.substr(0,2);
    var m = str.substr(2,2);
    chgVal = h + ":" + m;
  }

  return chgVal
}
 
/**************************
 * コロン編集を解除するFunction
 **************************/
private offColon(value: string){
  const reg = new RegExp(":", "g");
  let chgVal: string = value;
  chgVal = value.replace(reg, "");
  return chgVal
}
}
</script>