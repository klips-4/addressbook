<template src="./template.html">

</template>

<script>


export default {
  name: "NotificationPage",
  props: {
    messages: {
      type: Array,
      default: () => {
        return []
      }
    },
    rightButton: {
      type: String,
      default: ''
    },
    leftButton: {
      type: String,
      default: ''
    },
    timeout: {
      type: Number,
      default: 3000
    }
  },
  data() {
    return {}
  },
  methods: {
    hideNotification() {
      let vm = this;
      if (this.messages.length) {

        setTimeout(function () {
          vm.messages.splice(vm.messages.length - 1, 1)
        }, vm.timeout)
      }
    }
  },
  watch: {
    messages() {
      this.hideNotification()
    }
  },
  mounted() {
    this.hideNotification()
  }
}
</script>


<style scoped lang="less" src="./style.less">

</style>