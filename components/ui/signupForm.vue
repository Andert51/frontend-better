<template>
  <v-card width="1000" color="#257180">
    <v-card-title>
      <p class="text-center" style="width:100% !important; color:#F2E5BF;">
        Welcome to PCF Registration Page
      </p>
    </v-card-title>
    <v-card-text>
      <v-form>
        <v-row>
          <v-col cols="4">
            <v-text-field
              v-model="user.name"
              dense
              outlined
              label="Name"
              placeholder="Write your name"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="user.patsur"
              dense
              outlined
              label="Patsurn"
              placeholder="Write your paternal Surname"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="user.matsur"
              dense
              outlined
              label="Matsurn"
              placeholder="Write your maternal surname"
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="4">
            <v-text-field
              v-model="user.adress"
              dense
              outlined
              label="Address"
              placeholder="Write your address"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="user.city"
              dense
              outlined
              label="City"
              placeholder="Write your city"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="user.state"
              dense
              outlined
              label="State"
              placeholder="Write your state"
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="4">
            <v-text-field
              v-model="user.phone"
              dense
              outlined
              label="Phone"
              placeholder="Write your phone"
            />
          </v-col>
          <v-col cols="4">
            <v-combobox
              v-model="user.rol"
              :items="['Admin', 'User', 'Guest', 'SuperAdmin', 'SuperUser', 'SuperGuest']"
              dense
              outlined
              label="Role"
              placeholder="Select your role"
            />
          </v-col>
          <v-col cols="4">
            <v-file-input
              v-model="user.image"
              dense
              outlined
              label="Image"
              placeholder="Write your image"
            />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="4">
            <v-text-field
              v-model="user.username"
              dense
              outlined
              label="Username"
              placeholder="Write your username"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="user.password"
              dense
              type="password"
              outlined
              label="Password"
              placeholder="Write your password"
            />
          </v-col>
          <v-col cols="4">
            <v-text-field
              v-model="confirmPassword"
              dense
              type="password"
              outlined
              label="Confirm Password"
              placeholder="Rewrite your password"
            />
          </v-col>
        </v-row>
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-row align="center" justify="center" class="ma-3">
        <v-btn color="#FD8B51" @click="gotoLogin">
          <span style="text-transform: none; color: #257180;">
            Cancel
          </span>
        </v-btn>
        <v-btn color="#FD8B51" class="ml-3" @click="registerUser">
          <span style="text-transform: none; color: #257180;">
            Register
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
      user: {},
      confirmPassword: ''
    }
  },
  methods: {
    gotoLogin () {
      this.$router.push('/')
    },
    async registerUser () {
      if (this.user.password === this.confirmPassword) {
        // eslint-disable-next-line no-console
        console.log('@Nint user =>', this.user)
        const response = await this.$axios.post('/employee/create', this.user, {
          headers: {
            'Content-Type': 'application/json'
          }
        })
        // eslint-disable-next-line no-console
        console.log('@Nint response =>', response)
      }
    }
  }

}
</script>

<style scoped>

</style>
