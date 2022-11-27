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
      default: 'Ok'
    },
  },
  data() {
    return {}
  },
  methods: {
    deleteNotification() {
      let vm = this;
      vm.messages.splice(vm.messages.length-1,1)
    }
  }
}
</script>


<style scoped lang="less" src="./style.less">

</style>