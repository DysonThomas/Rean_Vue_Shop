<template>
  <div class="hello">
    <nav class="navbar custom-nav fixed-top navbar-expand-lg navbar-light ">
      <div class="container">
        <router-link class="navbar-brand" to="/">Vue Shop</router-link>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mr-auto">
          </ul>
          <form class="form-inline my-2 my-lg-0">
            <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
            <b-button variant="success" v-b-modal.modal-1>Get Start</b-button>

            <a class="btn btn-outline-success border-0 mx-2 my-2 my-sm-0" data-toggle="modal" data-target="#miniCart">
              <i class="fas fa-cart-plus"></i>
            </a>
            <a class="btn btn-outline-success border-0  my-2 my-sm-0" data-toggle="modal" data-target="#miniCart">
              <i class="fa fa-users" aria-hidden="true"></i>
            </a>
          </form>
        </div>

        <!-- Modal -->
        <b-modal id="modal-1" title="Welcome To Vue Shop" hide-footer="true">
          <div>
            
            <b-tabs content-class="mt-3" align="center">
              <b-tab title="Login" active>
                <!-- <img class="modal-img" src="../assets/Images/2.jpg"> -->
              
                  <form>
                    <div class="form-group">
                      <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp"
                        placeholder="Enter email"  required>
                    </div>
                    <div class="form-group">
                      <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password" required>
                    </div>
                    <button type="submit" class="btn btn-primary mr-2">Sign In</button>
                    <button type="submit" @click="close" class="btn btn-primary">Close</button>
                  </form>
                
              </b-tab>
              <b-tab title="Sign Up">
                  <form>
                         <div class="form-group">
                    <input type="text" class="form-control" placeholder="Enter Your Name" required>  
                         </div>
                    <div class="form-group"> 
                      
                      <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp"
                        placeholder="Enter email" required>
                    </div>
                    <div class="form-group">
                      <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password" required>
                    </div>
                    
                    
                    <button type="submit" class="btn btn-primary mr-2">Sign Up</button>
                    <button type="submit" @click="close"  class="btn btn-primary">Close</button>
                  </form>
                </p>
              </b-tab>
            </b-tabs>
          </div>
        </b-modal>
      </div>

    </nav>


  </div>
</template>

<script>
  export default {
    name: "Navbar",
    props: {
      msg: String
    },
    methods:{
      close(){
        this.$bvModal.hide('modal-1')
      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @media (min-width: 992px) {

    .navbar.custom-nav {
      padding-top: 16px;
      padding-bottom: 16px;
      background-color: #0000000f !important;
    }
    form{
      text-align: center;
    }
    .modal-img{
      width: 20%;
    }

  }
</style>