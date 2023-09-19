<template>
  <div class="container">
    <div class="header">
      <Header />
    </div>

    <div class="sidebar">
      <Sidebar />
    </div>
    <div></div>
    <div class="upload-content">
      <div class="title">
        <div class="title_text">Lettuce disease</div>
      </div>
      <div class="preview">
        <div class="text-center">
          <h2 class="text-3xl font-bold text-gray-900" style="height: 10%">
            File Upload!
          </h2>
          <p class="mt-2 text-sm text-gray-400" style="height: 7%">
            Put your leaf into here
          </p>
          <div class="mt-3 space-y-3">
            <div class="" style="height: 70%">
              <label
                class="text-sm font-bold text-gray-500 tracking-wide"
                style="height: 5%"
                >Attach Document</label
              >
              <div
                class="flex items-center justify-center w-full"
                style="flex-direction: column"
              >
                <label
                  class="flex flex-col rounded-lg border-4 border-dashed w-full h-60 group text-center"
                >
                  <div
                    class="h-full w-full text-center flex flex-col md:items-center justify-center"
                  >
                    <div
                      class="flex flex-auto justify-center max-h-48 w-4_5 md:w-2_5 mx-auto"
                    >
                      <img
                        v-if="!item.imageUrl"
                        class="has-mask h-36 object-center"
                        src="https://img.freepik.com/free-vector/image-upload-concept-landing-page_52683-27130.jpg?size=338&ext=jpg"
                        alt="freepik image"
                      />
                      <img
                        v-if="item.imageUrl"
                        class="has-mask h-36 object-center"
                        :src="item.imageUrl"
                      />
                    </div>
                  </div>
                  <input type="file" accept="image/*" @change="onChange" />
                </label>
                <div style="height: 10%; margin-top: 20px;" v-if="result.name !== ''">
                  <span
                    >Result: I found from your {{ result.name }} leaf
                     {{ result.disease }} disease.</span
                  >
                </div>
                <div style="height: 10%; margin-top: 20px" v-if="result.name === ''">
                  <span
                    >Upload image and press check button and wait in second</span
                  >
                </div>
              </div>
              <button class="btn_check" @click="checkImage()">Check</button>
              <div style="height: 10%">
                <p class="text-sm text-gray-300" style="height: 10%">
                  <span>File type allow: .png, .jpg</span>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="footer">
      <Footer />
    </div>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import Sidebar from "../components/Sidebar.vue";
import Footer from "../components/Footer.vue";
import axios from "axios";

export default {
  components: {
    Header,
    Sidebar,
    Footer,
  },
  name: "imageUpload",
  data() {
    return {
      item: {
        //...
        image: null,
        imageUrl: null,
        info: null,
      },
      result: { name: "", disease: "" },
    };
  },
  methods: {
    checkImage() {
      axios;
      var bodyFormData = new FormData();
      bodyFormData.append("file", this.image);
      // const agent = new https.Agent({
      //     rejectUnauthorized: false
      // });
      axios({
        method: "post",
        url: "http://localhost:5001/api/predict-diseases",
        data: bodyFormData,
        headers: {
          "Content-Type": "multipart/form-data",
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Methods": "GET,PUT,POST,DELETE,PATCH,OPTIONS",
        },
        // httpsAgent: agent
      })
        .then((res) => {
          console.log(res);
          this.result = res.data;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    onChange(e) {
      const file = e.target.files[0];
      this.image = file;
      this.item.imageUrl = URL.createObjectURL(file);
    },
  },
};
</script>

<style scoped>
.btn_check {
  height: 30px;
  width: 100px;
  background-color: #2563eb;
  color: aliceblue;
}

.text-center {
  text-align: center;
}

.text-3xl {
  font-size: 1.875rem;
}

.font-bold {
  font-weight: bold;
}

.text-gray-900 {
  color: #111827;
}

.mt-2 {
  margin-top: 0.5rem;
}

.text-sm {
  font-size: 0.875rem;
}

.text-gray-400 {
  color: #6b7280;
}

.mt-3 {
  margin-top: 0.75rem;
}

.space-y-3 > * + * {
  margin-top: 0.75rem;
}

.grid {
  display: grid;
}

.grid-cols-1 {
  grid-template-columns: repeat(1, minmax(0, 1fr));
}

.space-y-2 > * + * {
  margin-top: 0.5rem;
}

.text-gray-500 {
  color: #6b7280;
}

.tracking-wide {
  letter-spacing: 0.025em;
}

.flex {
  display: flex;
}

.items-center {
  align-items: center;
}

.justify-center {
  justify-content: center;
}

.w-full {
  width: 100%;
}

.rounded-lg {
  border-radius: 0.5rem;
}

.border-4 {
  border-width: 0.2rem;
}

.border-dashed {
  border-style: dashed;
}

.h-60 {
  height: 19rem;
}

.p_20 {
  padding: 20px;
}

.md\:p-5 {
  padding: 1.25rem;
}

.group {
  position: relative;
}

.text-center {
  text-align: center;
}

.h-full {
  height: 100%;
}

.w-full {
  width: 100%;
}

.flex-auto {
  flex: 1;
}

.max-h-48 {
  max-height: 18rem;
}

.w-4-5 {
  width: 80%;
}

.w-2_5 {
  width: 40%;
}

.mx-auto {
  margin-left: auto;
  margin-right: auto;
}

.mt-3 {
  margin-top: -0.75rem;
}

.has-mask {
  mask-image: none;
}

.object-center {
  object-position: center center;
}

.pointer-none {
  pointer-events: none;
}

.text-gray-500 {
  color: #6b7280;
}

.text-sm {
  font-size: 0.875rem;
}

.text-blue-600 {
  color: #2563eb;
}

.hover\:underline:hover {
  text-decoration: underline;
}

/* Additional styles for file input */
input[type="file"] {
  display: none;
}

.title {
  height: 8%;
  border-radius: 8px;
  background-color: lightblue;
  /* margin-top: 30px; */
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  width: 30%;
}

.title_text {
  display: flex;
  font-size: 40px;
  font-weight: 700;
  flex-direction: column;
  color: blue;
  align-content: center;
  justify-content: center;
  align-items: center;
}

* {
  /* padding: 0;
        margin: 0; */
  font-family: Merriweather;
  font-size: 16px;
  height: 100%;
}

.container {
  display: grid;
  grid-template-columns: 100px 1fr;
  grid-template-rows: 50px 1fr 50px;
  grid-template-areas:
    "header header"
    "sidebar upload-content"
    "sidebar footer";

  grid-gap: 0;
  min-height: 100vh;
  background-color: white;
}

.header {
  grid-area: header;
}

.sidebar {
  grid-area: sidebar;
}

.footer {
  grid-area: footer;
}

.upload-content {
  grid-area: upload-content;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  background-image: url(../assets/img/green-leaf.jpg);
}

.preview {
  height: 70%;
  width: 30%;
  margin-top: 5%;
  background-color: white;
  border-radius: 10%;
}

.preview input {
  width: 100%;
}

/* .preview img {
    } */
</style>
