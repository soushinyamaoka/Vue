<template>
  <div>
    <Header></Header>
    <div>
      <CustomInput
        :pValue="count"
        @input="count = $event"
      ></CustomInput>
      <CustomButton
        @click="countUpEvent()"
      ></CustomButton>
    </div>
    <div>
      <TimeInput
        :pValue="time"
        @onChange="time = $event"
      ></TimeInput>
    </div>
    <label for="">現在のdataの値</label>
    <div>
      <table border="1">
        <tr>
          <th>count</th>
          <th>{{count}}</th>
        </tr>
        <tr>
          <td>time</td>
          <td>{{time}}</td>
        </tr>
      </table>
    </div>
    <Footer></Footer>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import TimeInput from "@/components/TimeInput.vue";
import CustomInput from "@/components/CustomInput.vue";
import CustomButton from "@/components/CustomButton.vue";

@Component({
  components: {
    Header,
    Footer,
    TimeInput,
    CustomInput,
    CustomButton,
  },
})
export default class Test001 extends Vue {
  count: number = 0;
  protected time: string = "12:12";

  protected countUpEvent() {
    this.count = isNaN(this.count) ? this.count : Number(this.count) + 1;
  }
}
</script>