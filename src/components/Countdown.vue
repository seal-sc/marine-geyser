<template>
  <div class="countdown-div">
    <b class="countdown-txt">{{ d }}{{ $t("date.day") }}</b>
    <b class="countdown-txt">{{ h }}</b>:
    <b class="countdown-txt">{{ m }}</b>:
    <b class="countdown-txt">{{ s }}</b>
  </div>
</template>

<script>
export default {
  name: 'Countdown',
  props: ["dateTime"],
  data() {
    return {
      d: '',
      h: '',
      m: '',
      s: '',
    }
  },
  created() {
    this.countTime()
  },
  methods: {
    countTime() {
      let date = new Date()
      let now = date.getTime()
      let endDate = new Date(this.dateTime)
      let end = endDate.getTime()

      let leftTime = end - now

      if (leftTime >= 0) {
        this.d = Math.floor(leftTime / 1000 / 60 / 60 / 24)
        this.h = Math.floor((leftTime / 1000 / 60 / 60) % 24)
        this.m = Math.floor((leftTime / 1000 / 60) % 60)
        this.s = Math.floor((leftTime / 1000) % 60)
      }

      this.h = (this.h < 10) ? "0" + this.h : this.h
      this.m = this.m < 10 ? "0" + this.m : this.m
      this.s = this.s < 10 ? "0" + this.s : this.s

      setTimeout(this.countTime, 1000)
    },
  },
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@import "../styles/colors.scss";
@import "../styles/fonts.scss";

.countdown-div {

}
</style>
