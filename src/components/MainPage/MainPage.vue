<template src="./template.html">

</template>

<script>
import {AuthHelpers} from "@/helpers/AuthHelpers";
import AddForm from "@/components/AddForm/AddForm";
import Contact from "@/components/Contact/Contact";
import SourceService from "@/services/SourceService";

export default {
  name: "MainPage",
  components: {AddForm, Contact},
  data(){
    return{
      addFormVisible: false,
      items: [],
      source: new SourceService({endpoint: 'Contact'}),
      telephone:'',
      addSendTelephone: false
    }
  },
  beforeMount() {
    this.getItems();
  },
  methods: {
    logout() {
      AuthHelpers.logout();
    },
    changeAddFormVisible() {
      this.addFormVisible = !this.addFormVisible;
    },
    getItems() {
      this.source.list().then((result) => {
        if (result.success) {
          this.items = result.data;
        }
      });
    },
    changeAddFormTelephone() {
      this.addSendTelephone = !this.addSendTelephone;
    },
  },
  computed: {
    userName() {
      const userData = AuthHelpers.getUserInfo();
      return userData.surname + ' ' + userData.name;
    }
  },
}
</script>

<style scoped src="./style.less" lang="less">
</style>