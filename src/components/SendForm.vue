<template>
  <main class="container-fluid overflow-scroll">
    <div class="card" v-for="message in messages" v-bind:key="message">
      <div class="card-body" >
        {{ message.text }}
      </div>
    </div>

  </main>

  <footer class="footer mt-auto py-3 bg-light">
    <div class="container">

      <div class="row" >

        <div class="col-9">
          <label for="message" class="visually-hidden">Message</label>
          <input type="text" v-model="message" v-on:keyup.enter="sendMessage()" class="form-control" id="message" placeholder="Type here a message">
        </div>
        <div class="col-1">
          <button type="button" v-on:click="sendMessage" class="btn btn-primary">Send</button>
        </div>
      </div>
    </div>
  </footer>

</template>

<script>
export default {
  name: 'SendForm',
  props: {
    msg: String
  },
  data() {
    return {
      message: "",
      messages: []
    }
  },
  methods: {
    sendMessage: function () {
      if(this.message) {
        this.messages.push({text: this.message});
        //todo add sending

        this.message = '';
      }
    }
  }

}
// let m = [{text:"hi there is someone touch"}, {text:"ok, thanks"}];

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import 'https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css';

body {
  height: 100%;
}

.h-100 {
  height: 100% !important;
}

main {
  min-height: 30%;
}
</style>
