<template>
  <!-- SOME FORM ELEMENTS HERE -->
  <div>
    <dropzone
      ref="myVueDropzone"
      :options="dropzoneOptions"
      @vdropzone-error="errorUploading"
      @vdropzone-success="fileUploaded"
      @vdropzone-queue-complete="submitForm"
      @vdropzone-sending="sending"
    />
    <button @click="saveForm">Save</button>
  </div>
</template>
<script>
import { mapActions, mapState, mapGetters } from "vuex";
export default {
  data: function () {
    return {
      dropzoneOptions: {
        url: "https://httpbin.org/post",
        thumbnailWidth: 150,
        maxFilesize: 0.5,
        headers: { "My-Awesome-Header": "header value" },
      },
      formData: {},
    };
  },
  computed: {
    ...mapState(["subjectFileUploadResponse"]),
  },
  methods: {
    ...mapActions(["subjectFileUpload"]),

    async saveForm() {
      // if (this.$refs.myVueDropzone.getQueuedFiles().length) {
      //   this.$refs.myVueDropzone.processQueue()
      // } else {
      //   this.submitForm()
      // }
      console.log(this.$refs.myVueDropzone);
      await this.subjectFileUpload(this.formData);
    },
    errorUploading(file, message, xhr) {
      // do something when a file errors
      // perhaps show a user a message and create a data element to stop form from processing below?
      console.log("error uploading", file);
    },
    fileUploaded(file, response) {
      // do something with a successful file upload. response is the server response
      // perhaps add it to your form data?
      console.log("From file upload", file);
      console.log("response :>> ", response);
    },
    submitForm() {
      // Queue is done processing (or nothing to process), you can now submit your form
      // maybe check for errors before doing the below step
      // do what ever you need to submit your form this.$axios.post(...) etc.
    },
    sending(file, xhr, formData) {
      console.log(formData);
      formData.append("file", file);
      console.log("formData :>> ", formData);
      this.formData = formData;
    },
  },
};
</script>