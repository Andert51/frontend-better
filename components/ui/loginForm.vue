<template>
  <v-card width="400" color="#257180">
    <v-card-title>
      <p class="text-center" style="width:100% !important; color:#F2E5BF;">
        Welcome to PCF Official Website
      </p>
    </v-card-title>
    <v-card-text>
      <v-row style="width: 100% !important;">
        <v-col cols="4" align-self="center">
          <v-img
            :src="require('@/assets/images/Tv.png')"
            style="width:150%"
          />
        </v-col>
        <v-col>
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
            <v-row v-if="errorMessage" class="error">
              {{ errorMessage }}
            </v-row>
          </form>
        </v-col>
      </v-row>
    </v-card-text>
    <v-card-actions>
      <v-row align="center" justify="center" class="ma-3">
        <v-btn color="#FD8B51" @click="gotoSignUp">
          <span style="text-transform: none; color: #257180;">
            Sign Up
          </span>
        </v-btn>
        <v-btn color="#FD8B51" class="ml-3" @click="login">
          <span style="text-transform: none; color: #257180;">
            Log In
          </span>
        </v-btn>
      </v-row>
    </v-card-actions>
  </v-card>
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
        if (res.data.success) {
          this.$router.push('/dashboard')
        }
      } catch (error) {
        this.errorMessage = error
      }
    },
    gotoSignUp () {
      this.$router.push('/signup')
    }
  }
}
</script>

<style scoped>
.error {
    color: red;
    margin-top: 10px;
}
</style>
