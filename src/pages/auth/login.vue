<template>
  <q-layout view="lHh Lpr lFf">
    <q-page-container>
      <q-page class="flex items-end justify-end" style="background-image: url('statics/img/bg-login.jpg">

          <div style="margin:100px;width:300px">
              <div class="row log-mar-bot">
                  <div class="col-4">
                    <q-card class="log-card">
                        <div style="padding:9px">
                            <b>Username</b>
                        </div>
                    </q-card>
                  </div>
                  <div class="col-1" style="width: 3%"></div>
                  <div class="col">
                      <q-input bg-color="primary" outlined v-model="text" dense="true" />
                  </div>
              </div>
              <div class="row log-mar-bot">
                  <div class="col-4">
                    <q-card class="log-card">
                        <div style="padding:9px">
                            <b>Password</b>
                        </div>
                    </q-card>
                  </div>
                  <div class="col-1" style="width: 3%"></div>
                  <div class="col">
                      <q-input bg-color="primary" outlined v-model="text" dense="true" />
                  </div>
              </div>
              <div class="row">
                <q-btn color="amber-6" @click="login()" text-color="black" label="Login" no-caps style="width:100%"/>
              </div>
          </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>
<style>
.q-field--outlined .q-field__control:before {
  border: 2px solid rgba(255,192,0);
}
.q-field--outlined .q-field__control:after {
  border: 2px solid rgba(255,192,0);
}
.q-field__control {
    color: rgba(255,192,0);
}
</style>
<script>
export default {
    data() {
        return {
            text : ''
        }
    },
    methods : {
        login(){
            this.$router.push('/')
        }
    }
}
</script>