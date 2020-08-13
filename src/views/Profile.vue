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
                      <input type="text" name="" v-model="profile.name" placeholder="Full name" class="form-control">
                    </div>
                  </div>

                  <div class="col-md-6">
                    <div class="form-group">
                      <input type="mobile" v-model="profile.phone" placeholder="Phone" class="form-control">
                    </div>
                  </div>

                  <div class="col-md-12">
                    <div class="form-group">
                      <input type="text" @keyup.enter="pinsearch" v-model="profile.postCode"
                        placeholder="Pincode (Press Enter Key For Auto Fill)" class="form-control">

                    </div>
                  </div>
                  <div class="col-md-12">
                    <div class="form-group">
                      <input type="text" v-model="profile.address" placeholder="housename" class="form-control">
                    </div>
                  </div>
                  <div class="col-md-12 col-lg-4">
                    <div class="form-group">
                      <input type="text" v-model="profile.city" placeholder="City" class="form-control">
                    </div>
                  </div>
                  <div class="col-md-12 col-lg-4">
                    <div class="form-group">
                      <input type="text" v-model="profile.district" placeholder="District" class="form-control">
                    </div>
                  </div>
                  <div class="col-md-12 col-lg-4">
                    <div class="form-group">
                      <input type="text" v-model="profile.state" placeholder="State" class="form-control">
                    </div>
                  </div>



                  <div class="col-md-12">
                    <div class="form-group">
                      <input type="submit" @click="updateProfile" value="Save Changes"
                        class="btn btn-primary mt-2 w-100">
                    </div>
                    <div class="form-group">
                      <input type="submit" @click="logout" value="Logout" class="btn btn-danger mt-2 w-100">
                    </div>
                  </div>

                </div>
              </div>

            </form>

          </b-tab>
          <b-tab title="Orders">


          </b-tab>
        </b-tabs>
      </div>
      <!-- <div class="container">
          
        <div class="intro h-100">
            <div class="row h-100 align-items-center">
              <div class="col-md-6 ml-3">
                    <h3>Profile settings</h3>
                    
                 <p>
                   Change your profile settings here
                 </p>
              </div>
              <div class="col-md-5">
                  <img src="/img/svg/profile.svg" width="300" alt="" class="img-fluid">
              </div>
            </div>
          </div>


          <div class="profile-content">

          <ul class="nav nav-pills ml-3" id="myTab" role="tablist">

            <li class="nav-item">
              <a class="nav-link active" id="profile-tab" data-toggle="tab" href="#profile" role="tab" aria-controls="profile" aria-selected="true">Profile</a>
            </li>

            <li class="nav-item">
              <a class="nav-link"  id="account-tab" data-toggle="tab" href="#account" role="tab" aria-controls="account" aria-selected="false">Account settings</a>
            </li>
           
          </ul>

            <div class="tab-content" id="myTabContent">
                <div class="tab-pane fade show active pt-3" id="profile" role="tabpanel" aria-labelledby="profile-tab">

                  <div class="container">
                      <div class="row">
                        
                        <div class="col-md-6">
                          <div class="form-group">
                            <input type="text" name="" v-model="profile.name" placeholder="Full name" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-6">
                          <div class="form-group">
                            <input type="text"  v-model="profile.phone" placeholder="Phone" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-12">
                          <div class="form-group">
                            <input type="text"  v-model="profile.address" placeholder="Address" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-8">
                          <div class="form-group">
                            <input type="text"  v-model="profile.postCode" placeholder="Postcode" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-4">
                          <div class="form-group">
                              <input type="submit" @click="updateProfile" value="Save Changes" class="btn btn-primary w-100">
                          </div>
                        </div>

                      </div>
                  </div>
                
                </div>

                <div class="tab-pane fade pt-3" id="account" role="tabpanel" aria-labelledby="account-tab">
                  <div class="container">
                      <div class="row">
                        <div class="col-md-">
                            <div class="alert alert-info">
                              Please use the Reset password email button for reseting the password. The form doens't work currently
                            </div>
                        </div>
                        <div class="col-md-6">
                          <div class="form-group">
                            <input type="text"  v-model="account.name" placeholder="User name" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-6">
                          <div class="form-group">
                            <input type="text"  v-model="account.email" placeholder="Email address" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-6">
                          <div class="form-group">
                            <input type="text"  v-model="account.password" placeholder="New password" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-6">
                          <div class="form-group">
                            <input type="text" v-model="account.confirmPassword"  placeholder="Confirm password" class="form-control">
                          </div>
                        </div>

                        <div class="col-md-4">
                          <div class="form-group">
                              <input type="file" @change="uploadImage" class="form-control">
                           </div>
                        </div>

                        <div class="col-md-4">
                          <div class="form-group">
                              <input type="submit" value="Save Changes" class="btn btn-primary w-100">
                          </div>
                        </div>

                        <div class="col-md-4">
                          <div class="form-group">
                              <input type="button" @click="resetPassword"value="Reset password email" class="btn btn-success w-100">
                          </div>
                        </div>
                      </div>
                  </div>
                </div>

            </div>
            
          </div>

      </div> -->


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
        info: null,
        profile: {
          name: null,
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
        const user = fb.auth().currentUser;
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
      // pinsearch() {
      //   axios.get(`https://api.postalpincode.in/pincode/`this.profile.postcode).then(response => (this.info = response))
      // }
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