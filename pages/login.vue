<template>
  <div class="login-page">
    <h2>Welcome</h2>
    <form>
      <v-row>
        <v-text-field
          v-model="form.username"
          outlined
          dense
        />
      </v-row>
      <v-row>
        <v-text-field
          v-model="form.password"
          outlined
          type="password"
          dense
        />
      </v-row>
      <v-rwo>
        <v-btn color="blue" @click="login">
          <span style="text-transform: none;">
            LogIn
          </span>
        </v-btn>
      </v-rwo>
      <v-row v-if="errorMessage" class="error">
        {{ errorMessage }}
      </v-row>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        username: '',
        password: ''
      },
      errorMessage: ''
    }
  },
  methods: {
    async login () {
      try {
        const res = await this.$auth.loginWith('local', {
          data: this.form
        })
        // eslint-disable-next-line no-console
        console.log('@res =>', res)
      } catch (error) {
        this.errorMessage = error
      }
    }
  }
}

</script>

<style scoped>
.login-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.login-page h2 {
  margin-bottom: 20px;
}

.error {
    color: red;
    margin-top: 10px;
}

</style>
