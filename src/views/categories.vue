<template>  
<div>
      <div class="row mt-4">
          <div class="col">
               <img @click="men" class="mg " src="../assets/Images/man.png" alt="">
              <p  @click="men" class=" mt-2 cate"><i class="fas fa-male"></i> Men</p>
          </div>
            <div class="col">
                <img @click="women" class="mg " src="../assets/Images/woman.png" alt="">
              <p @click="women" class=" mt-2 cate " > <i class="fas fa-female"></i> Women</p>
          </div>
           <div class="col">
                <img class="mg " src="../assets/Images/microchip.png" alt="">
              <p  class=" mt-2  cate " > <i class="fas fa-microchip"></i> Electronics</p>
          </div>
         
      </div>
    <div class="container">
      
      <div class="row mt-5 mb-3">
            
            <div class="col-lg-" v-for="product in products">
                  <div class="card">
                        <!-- <carousel :perPage="1">
                          <slide v-for="(image, index) in product.images">
                                <img :src="image" class="mt-5 card-img-top" alt="..." width="250px">
                          </slide>
                        </carousel> -->

                        <img :src=product.images[0] class="mt-5" alt="..." width="250px">
                        <div class="card-body">
                          <div class=" card-name justify-content-between">
                            <h5 class="card-title">{{ product.name }}</h5>
                          </div>
                          <h5 class="card-price">{{ product.price }}₹</h5>
                          <button class="btn btn-primary">Add To Cart</button>
                          
                        </div>
                    </div>
                </div>
             
      </div>
    </div>
</div>
     
 
</template>

<script>
import {db} from '../firebase';

export default {
name:"categories",
 firestore(){
      return {
        products: db.collection('products'),
      }
  },
  data(){
    return {
        products: [],
        selectedCategories:"",
    }
  },
  methods:{
    men(){
     
      this.selectedCategories="002"
      this.showProduct();
    },
    women(){
      this.selectedCategories="001"
      this.showProduct();
    },
    showProduct(){
      this.products.splice(0,this.products.length)
      db.collection("products").where("selected", "==", this.selectedCategories).get()
    .then((querySnapshot)=>{
        querySnapshot.forEach((doc)=>{ 
            this.products.push(doc.data())
            console.log(doc.id, " => ", doc.data());
        });
    })
    .catch(function(error) {
        console.log("Error getting documents: ", error);
    });
    }
  }
}
</script>

<style>
.mg{
    width: 70px;
}
.mg{
    cursor:pointer;
}
.cate{
      cursor:pointer;
}
/* .product-item{
    width: 100%;
} */
.card{
     border:none; 
    height: 100%;
   
    
}
.card-img-top{
    width: 50%;
} 
.card-title{
  font-size: 1rem;
}
.card-name{
  text-align: center;
}
</style>