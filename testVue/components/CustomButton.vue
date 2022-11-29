<template>
  <button
  class="btn btn--orange btn--circle btn--circle-a btn--shadow"
  @click="clickEvent()"
  >
  click
  </button>
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
  public clickEvent() {
    this.$emit('click')
  }
}
</script>
<style scoped>
/*主な共通部分は省略*/

.btn--orange {
  color: #fff;
  background-color: #eb6100;
}

.btn--orange:hover {
  color: #fff;
  background: #f56500;
}

.btn--shadow {
  -webkit-box-shadow: 0 3px 5px rgba(0, 0, 0, 0.3);
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.3);
}

.btn--circle {
  border-radius: 50%;
  width: 50px;
  height: 20px;
  padding: 0;
}
</style>