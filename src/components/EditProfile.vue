<template>
  <div>
    <div id="edit-profile">
      <h3 id="edit-title">Edit Profile</h3>
      <p>Update Email</p>
      <input type="email" id="email-input" v-model="email" />
      <p>Update Username</p>
      <input type="text" id="username-input" v-model="username" />
      <p>Update Password</p>
      <input type="text" id="password-input" v-model="password" />
      <p>Update Bio</p>
      <textarea type="text" id="bio-input" v-model="bio" />
      <p>Update Birthdate</p>
      <input
        type="text"
        id="birthdate-input"
        placeholder="yyyy-mm-dd"
        v-model="birthdate"
      />
      <br /><br />
      <button id="update-btn" @click="updateProfile">Update</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import cookies from "vue-cookies";

export default {
  name: "edit-profile",
  data() {
    return {
      email: "",
      username: "",
      password: "",
      bio: "",
      birthdate: ""
    };
  },
  methods: {
    updateProfile: function() {
      axios
        .request({
          method: "PATCH",
          url: "https://tweeterest.ml/api/users",
          headers: {
            "Content-Type": "application/json",
            "X-Api-Key": "QEYysOftSHseKha8slzLGq2WnFmPVmOqLvNJ5f45MEovC"
          },
          data: {
            loginToken: cookies.get("loginToken"),
            email: this.email,
            username: this.username,
            password: this.password,
            bio: this.bio,
            birthdate: this.birthdate
          }
        })
        .then(response => {
          console.log(response);
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<style lang="scss" scoped>
#edit-title {
  text-align: center;
  font-family: "Arimo", sans-serif;
  color: #783030;
  margin: 5vh;
  font-size: 24px;
}
#edit-profile {
  display: grid;
  align-items: center;
  justify-items: center;
  border: 1px solid black;
  width: 75%;
  margin-left: 12.5%;
  margin-top: 5vh;
}
p {
  font-family: "Arimo", sans-serif;
  color: #783030;
  margin: 1vh;
}
#birthdate-input {
  text-align: center;
}
input {
  margin: 1vh;
}
#update-btn {
  background-color: #f0f0f0;
  color: black;
  padding: 5px;
  border-radius: 7%;
  cursor: pointer;
  transform: perspective(1px) translateZ(0);
  transition-duration: 0.3s;
  transition-property: transform;
  margin-bottom: 10px;
}
#update-btn:hover {
  transform: scale(0.9);
}
#status {
  font-family: "Arimo", sans-serif;
  color: #783030;
  margin: 4vh;
}
</style>
