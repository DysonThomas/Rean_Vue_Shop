<template>
  <div class="products">
    <navbar></navbar>

    <div class="card">
      <div class="profile-tab">
        <b-tabs content-class="mt-2" align="center">
          <b-tab title="Profiles" active>
            <!-- <img class="modal-img" src="../assets/Images/2.jpg"> -->
            <form>
              <div class="container mt-5">
                <div class="row">

                  <div class="col-md-6">
                    <div class="form-group">
                      <input type="text" name="" v-model="profile.username" placeholder="Full name" class="form-control">
                    </div>
                  </div>

                  <div class="col-md-6">
                    <div class="form-group">
                      <input type="mobile" v-model="profile.phone" placeholder="Phone" class="form-control">
                    </div>
                  </div>
                   <div class="col-md-12">
                    <div class="form-group">
                      <input type="text" v-model="profile.address" placeholder="housename" class="form-control">
                    </div>
                  </div>

                  <div class="col-md-6">
                    <div class="form-group">
                      <input type="text" @keyup.space="pinsearch" v-model="profile.postCode"
                        placeholder="Pincode (Press Space Key For Auto Fill)" class="form-control">

                    </div>
                  </div>
                 
                  <div class="col-md-6 col-lg-6">
                    <div class="form-group">
                      <input type="text" v-model="profile.Block" placeholder="City" class="form-control">
                    </div>
                  </div>
                   <div class="col-md-12 col-lg-4">
                    <div class="form-group">
                      <input type="text" v-model="profile.Name" placeholder="PostOffice" class="form-control">
                    </div>
                  </div>
                  <div class="col-md-12 col-lg-4">
                    <div class="form-group">
                      <input type="text" v-model="profile.District" placeholder="District" class="form-control">
                    </div>
                  </div>
                  <div class="col-md-12 col-lg-4">
                    <div class="form-group">
                      <input type="text" v-model="profile.State" placeholder="State" class="form-control">
                    </div>
                  </div>



                  <div class="col-md-12">
                  
                      <button class="btn btn-primary" @click="updateProfile">
                        Save Changes
                      </button>
                       <button class="btn btn-danger ml-5" @click="logout">
                        Logout
                      </button>
            
                    
                  </div>

                </div>
              </div>

            </form>

          </b-tab>
          <b-tab title="Orders">


          </b-tab>
        </b-tabs>
      </div>
      


    </div>
  </div>
</template>

<script>
  import {fb,db} from '../firebase';
  import axios from 'axios';

  export default {
    name: "Profile",
    props: {
      msg: String
    },

    data() {
      return {
        user: "",
        info: {},
        profile: {
          sname: null,
          phone: null,
          address: null,
          postcode: null,
          city: "",
          district: "",
          state: ""
        },
      }
    },

    firestore() {
      const user = fb.auth().currentUser;
      return {
        profile: db.collection('profiles').doc(user.uid),
      }
    },
    methods: {
      updateProfile() {
        db.collection("profiles").doc(user.uid).set(
            this.profile
          )
          .then(function () {
            console.log("Document successfully written!");
          })
          .catch(function (error) {
            console.error("Error writing document: ", error);
          });
        alert("Sucess")
      },
      logout() {
        fb.auth().signOut()
          .then(() => {
            this.$router.replace('/');
          })
          .catch((err) => {
            console.log(err);
          });
      },
      pinsearch() {
        
        axios.get(`https://api.postalpincode.in/pincode/${this.profile.postCode}`).then(response => (this.profile = response.data[0].PostOffice[1]))

            
     },
    
    }

      // created(){
      //   const user = fb.auth().currentUser;
      //   console.log(user);
      //   this.profile.name=user.displayName;

      // }

    };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .profile-tab {
    padding-top: 10%;
  }

  .card {
    padding-top: 5%;
    padding-bottom: 5%;
    padding-right: 10%;
    padding-left: 10%;
  }
</style>