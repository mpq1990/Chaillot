<template>
  <div class="hello">
    <div class="holder">
      <form v-on:submit.prevent="submitForm">
        <input
          type="text"
          placeholder="Your first name..."
          v-validate="'required'"
          v-model="firstName"
          name="firstName"
        >
        <p class="alert" v-if="errors.has('firstName')">{{ errors.first('firstName') }}</p>

        <input
          type="text"
          placeholder="Your last name"
          v-model="lastName"
          v-validate="'required'"
          name="lastName"
        >
        <p class="alert" v-if="errors.has('lastName')">{{ errors.first('lastName') }}</p>

        <input
          type="text"
          placeholder="Your date of birth YYYY-MM-DD"
          v-model="dateOfBirth"
          v-validate="'required|date_format:yyyy-MM-dd'"
          name="dateOfBirth"
        >
        <p class="alert" v-if="errors.has('dateOfBirth')">{{ errors.first('dateOfBirth') }}</p>

        <input
          type="text"
          placeholder="Your city of birth..."
          v-model="cityOfBirth"
          name="cityOfBirth"
          v-validate="'required'"
        >
        <p class="alert" v-if="errors.has('cityOfBirth')">{{ errors.first('cityOfBirth') }}</p>

        <input
          type="text"
          placeholder="Your country of birth..."
          v-model="countryOfBirth"
          name="countryOfBirth"
          v-validate="'required'"
        >
        <p class="alert" v-if="errors.has('countryOfBirth')">{{ errors.first('countryOfBirth') }}</p>

        <input
          type="text"
          placeholder="Your native language..."
          v-model="nativeLanguage"
          name="nativeLanguage"
          v-validate="'required'"
        >
        <p class="alert" v-if="errors.has('nativeLanguage')">{{ errors.first('nativeLanguage') }}</p>

        <button v-on:click="submitForm">SUBMIT</button>
      </form>

      <!-- <ul>
        <li v-for="(data, index) in skills" :key="index">{{data.skill}}</li>
      </ul>-->
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      firstName: "",
      lastName: "",
      dateOfBirth: "",
      cityOfBirth: "",
      countryOfBirth: "",
      nativeLanguage: ""
    };
  },
  methods: {
    submitForm() {
      this.$validator.validateAll().then(
        result => {
          if (result) {
            console.log(result);
            console.log("submitting the form");
            console.log(this.firstName);
            console.log(this.lastName);
            console.log(this.dateOfBirth);
            console.log(this.cityOfBirth);
            console.log(this.countryOfBirth);
            console.log(this.nativeLanguage);
          } else {
            console.log("invalid");
          }
        },
        error => {
          console.log(error);
        }
      );
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  scoped>
.holder {
  background: #fff;
}
ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}
p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}
.container {
  box-shadow: 0px 0px 40px lightgray;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687f7f;
}

.alert {
  background: #fdf2ce;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin-top: -20px;
}
</style>
