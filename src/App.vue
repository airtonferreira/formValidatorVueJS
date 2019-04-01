<template>
<body>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-4 mt-5 bg-light rounded">
        <h1 class="text-center font-weight-bold text-info">Form Teste Sell2Brazil</h1>
        <hr class="bg-light">

        <form action="#" @submit.prevent="submit" method="post" id="form-box" class="p-2">
          <div class="form-group input-group">
            <div class="input-group-prepend">
              <span class="input-group-text">
                <i class="fas fa-user"></i>
              </span>
            </div>
            <input
              :class="{invalid: $v.name.$dirty && $v.name.$invalid}"
              @input="$v.name.$touch()"
              v-model="name"
              type="text"
              name="name"
              class="form-control"
              placeholder="Digite seu nome"
            >
          </div>

          <div class="form-group input-group">
            <div class="input-group-prepend">
              <span class="input-group-text">
                <i class="fas fa-phone"></i>
              </span>
            </div>
            <input
              :class="{invalid: $v.tel.$dirty && $v.tel.$invalid}"
              @input="$v.tel.$touch()"
              v-model="tel"
              type="tel"
              name="tel"
              class="form-control"
              placeholder="(DDD) 9xxxx-xxxx"
            >
          </div>

          <div class="form-group input-group">
            <div class="input-group-prepend">
              <span class="input-group-text">
                <i class="fas fa-envelope"></i>
              </span>
            </div>
            <input
              :class="{invalid: $v.email.$dirty && $v.email.$invalid}"
              @input="$v.email.$touch()"
              v-model="email"
              type="email"
              name="email"
              class="form-control"
              placeholder="seunome@email.com.br"
            >
          </div>

          <div class="form-group">
            <input
              type="submit"
              name="submit"
              id="submit"
              class="btn btn-success btn-block"
              value="Salvar dados"
            >
          </div>
        </form>

        <br>

        <div v-if="submit" class="print">
          <h3>Seus dados:</h3>
          <div>
            {{name}}
          </div>
          <div>
            {{tel}}
          </div>
          <div>
            {{email}}
          </div>
            
        </div>

      </div>
    </div>
  </div>
</body>
</template>

<script>
import { required } from "vuelidate/lib/validators";

export default {
  name: "app",
  data() {
    return {
      
      name: "",
      tel: "",
      email: ""
    };
  },
  methods: {
    submit() {
      if (this.isValid) {
        window.console.log(JSON.stringify(this.$data));
      } else {
        this.$v.$touch();
      }
    }
  },
  validations: {
    name: {
      required
    },
    tel: {
      required
    },
    email: {
      required
    }
  },
  computed: {
    isValid() {
      return (
        !this.$v.name.$invalid &&
        !this.$v.tel.$invalid &&
        !this.$v.email.$invalid
      );
    }
  }
};
</script>
