<template src="./template.html"/>

<script>
import SourceService from "@/services/SourceService";
import {AuthHelpers} from "@/helpers/AuthHelpers";


export default {
  name: "AddForm.vue",
  data() {
    return {
      surname: "",
      name: "",
      telephone: "",
      email: "",
      source: new SourceService({endpoint: 'Contact'})

    }
  },
  beforeMount() {
    this.source.create().then((result) => {
      if (result.success) {
        this.contacts = {...result.data};
      }
    });
  },
  methods: {
    submit() {
      const rec = {
        ...this.contacts, contact_name: this.name, user_id: AuthHelpers.getUser(), contact_surname: this.surname,
        telephone: this.telephone, email: this.email
      };
      this.source.update(rec).then((result) => {
        if (result.success) {
          this.surname = '';
          this.name = '';
          this.telephone = "";
          this.email = "";
          this.$emit('submit');
        }
      });
    }
  }
}
</script>

<style scoped src="./style.less" lang="less">
</style>