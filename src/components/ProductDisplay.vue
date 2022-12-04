<template>

<!--<div v-if="products.category === 'men\'s clothing' " class="background">
        <div  class="top-background background-men">
        <div class="background-men"></div> 
        <div class="featured-image"></div>
        </div>
        <div class="bottom-background"></div>
    </div>

    <div v-if="products.category === 'women\'s clothing' " class="background">
        <div  class="top-background background-women">
        <div class="background-men"></div> -->
 <!--       <div class="featured-image"></div>
        </div>
        <div class="bottom-background"></div>
    </div> -->
   
    <div  class="background">
        <div  class="top-background" :class="[
            products.category === 'men\'s clothing' ? 'background-men'
            : products.category === 'women\'s clothing' ? 'background-women'
            :  'background-misc'
        ]">
            <div :class="[
            products.category === 'men\'s clothing' ? 'featured-image'
            : products.category === 'women\'s clothing' ? 'featured-image'
            :  'featured-misc'
        ]"></div>
        </div>
        
        
        
    </div>

    <div class="group-4">
        
        
        <div class="rectangle-7" v-if="products.category === 'men\'s clothing' || products.category === 'women\'s clothing'">
            <div v-if="products" class="intersect">
                <img class="product-image" :src = "products.image" />
            </div>

                <div class="group-7">

                    <div v-if="products" class="atas">
                        
                        <h1 class="product-title" :class="[
                                products.category === 'men\'s clothing' ? 'product-title-men'
                                : products.category === 'women\'s clothing' ? 'product-title-women'
                                :  'there-is-no-product'
                            ]">
                            {{products.title}}
                        </h1>
                        <!-- <h1>aaaa</h1> -->
                    
                        <div class="title-description">
                            <div class="left">
                                <p>{{products.category}}</p>
                            </div>
                            <div v-if="(products.rating != undefined)" class="right" :class="[
                                products.category === 'men\'s clothing' ? 'rating-men'
                                : 'rating-women'
                            ]">
                                <p>{{products.rating.rate}}/5</p>
                                <div class="review-image">
                                    <div :class="[products.rating.rate > 0 ? 'ellipse-colored' : 'ellipse-white']" ></div>
                                    <div :class="[products.rating.rate > 1 ? 'ellipse-colored' : 'ellipse-white']" ></div>
                                    <div :class="[products.rating.rate > 2 ? 'ellipse-colored' : 'ellipse-white']" ></div>
                                    <div :class="[products.rating.rate > 3 ? 'ellipse-colored' : 'ellipse-white']" ></div>
                                    <div :class="[products.rating.rate > 4 ? 'ellipse-colored' : 'ellipse-white']"></div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="garis-pembatas"></div>

                    <div v-if="products" class="tengah">
                        <div class="description">
                            <p>{{products.description}}</p>
                        </div>
                        
                        
                    </div>

                    <div class="garis-pembatas"></div>

                    <div v-if="products" class="agak-bawah">
                        <div class="price" :class="[
                                products.category === 'men\'s clothing' ? 'product-title-men'
                                : products.category === 'women\'s clothing' ? 'product-title-women'
                                :  'there-is-no-product'
                            ]">
                            <p>${{products.price}}</p>
                        </div>
                    </div>

                    <div v-if="products.category === 'men\'s clothing' " class="bawah">
                        
                        <button types="button" id="btn-counter" class="buy-now men-blue"><a>Buy Now</a></button>
                        <div class="loading">
                            <!-- <input type="checkbox"/> -->
                            <button types="button" id="btn-counter" @click="nextProduct()" class="next-product men-blue"><a>Next Product</a></button>
                        </div>
                        <!-- <div v-for="product in products" :id="product.id" class="count"> -->
                            
                        <!-- </div> -->
                        
                    </div>

                    <div v-else-if="products.category === 'women\'s clothing' " class="bawah">
                        <button types="button" id="btn-counter" class="buy-now women-pink"><a>Buy Now</a></button>
                        <button types="button" id="btn-counter" @click="nextProduct()" class="next-product women-pink"><a>Next Product</a></button>
                    </div>

                </div>
        </div>

        <div v-else class="rectangle-7 unavailable">
           
                <p>This product is unavailable to show</p>
                <div class="bawah">
                         
                    <button types="button" id="btn-counter" @click="nextProduct()" class="next-product unavailable"><a>Next Product</a></button>
                    
                    <!-- <div v-for="product in products" :id="product.id" class="count"> -->
                        
                    <!-- </div> -->
                    
                </div>
                <img /> 
        </div>
        
        <div class="loader"></div>
        

        <!-- <div v-if="products category !== 'men\'s clothing' || 'women\'s clothing'"></div> -->
    </div>

</template>

<script>
import { createDOMCompilerError } from '@vue/compiler-dom';



export default{
    data(){
        // url: 'https://fakestoreapi.com/products/1';
        return{
            products: [],
            id : 1
        }
    },
    methods: {
       

       
        // fetch('https://fakestoreapi.com/products/' + this.id)
        //     .then(res=>res.json())
        //     .then((data) => {this.products = data;
        //                 console.log(this.products);
        // })
        async show(){            
            try {
                const response = await fetch('https://fakestoreapi.com/products/' + this.id)
                // const { data: products } = await response.json()
                const data = await response.json()
                console.log(data)
                this.products = data
            } catch(err) {
                console.log("Haha")
                this.id = 1
                this.show()
            }            
        }, 
          

        nextProduct(){
            this.id++;
            this.show()
        },
    },
    

    async created(){
        console.log(this.id);
        const data = await this.show()
    },
    
}
</script>

<style scoped>
a{
    cursor: pointer;
}

/* kotak tengah */
.group-4 {
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    /* top: 117px; */
}

.rectangle-7{
  display: grid;
  grid-template-columns: 35% auto;
  /* grid-template-rows: 25% 50% 25%; */
  /* display: flex;
  flex-direction: column; */
  position: absolute;
  /*min-width: 1034px;*/
  max-width: 1034px;
  width: 70%;
  height: 580px;
  /* left: 55px; */
  top: 117px;
  /* justify-content: center; */
  
  background: #FFFFFF;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  
   
}

/* isi kotak tengah */
.group-7{
  display: flex;
  flex-direction: column;
  padding: 50px 56px 46px 0px;
  color:black;
  justify-content: space-around;
  /* align-items: center; */
}

.atas{
    display: flex;
    flex-direction: column;
    

}

.product-title{
    /* position: absolute; */
    max-width: 548px;
    max-height: 68px;
    /* left: 577px;
    top: 176px; */

    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 28px;
    line-height: 34px;
    /* justify-content: center; */
}

.product-title-men{
    color: #002772;
}

.product-title-women{
    color: #720060;
}

.there-is-no-product{
    color: black;
}

.title-description{
  display:flex;
  justify-content: space-between;
  margin-top: 25px;
  font-family: 'Inter';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 22px;



    color: #3F3F3F;

}


/* rating */
.right{
    display: flex;
    flex-direction: row;
    
    gap: 5px;
}

.review-image{
    display: flex;
    flex-direction: row;
    gap: 1px;
}

.ellipse-white{
    box-sizing: border-box;

    /* position: absolute; */
    width: 18px;
    height: 18px;
    /* left: 1074px; */
    top: 226px;
    border-radius: 10px;
    /* background: #FFFFFF; */
}

.ellipse-colored{
    box-sizing: border-box;

    /* position: absolute; */
    width: 18px;
    height: 18px;
    /* left: 1074px; */
    top: 226px;
    border-radius: 10px;
}
.rating-men .ellipse-white{
    border: 1px solid #002772;
}

.rating-women .ellipse-white{
    border: 1px solid #720060;
}

.rating-men .ellipse-colored{
    background-color:#002772;
}

.rating-women .ellipse-colored{
    background-color: #720060;
}

/* lanjut konten */
.tengah{
    display: flex;
    flex-direction: column;
    /* justify-content: space-around; */
   
    align-items: center;
    justify-content: center;
}

.description{
    max-height: 163px;
    max-width: 517px;
    overflow: scroll;
}
.description p{
    /* position: absolute; */
    
    
    /* left: 577px;
    top: 328px; */

    font-family: 'Inter';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;

    color: #1E1E1E;
    
   
}

.agak-bawah{
    display: flex;
}

.price{
    width: 97px;
    height: 34px;
    /* left: 577px; */
    top: 569px;

    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 28px;
    line-height: 34px;
}

.bawah{
  display: flex;
  justify-content: flex-end;
  /* padding-right: 67px; */
}

.garis-pembatas{
    /* position: absolute; */
    /* display: flex; */
    width: 100%;
    height: 0px;
    /* justify-content: space-between; */
    /* left: 577px; */
    /* top: 302px; */

    border: 1px solid rgba(0, 0, 0, 0.2);
}

.buy-now{
  /* background-color: #720060; */
  border-radius: 4px;
  /* color: white; */
  min-height: 42px;
  min-width: 259px;
  left: 577px;
  top: 618px;
  font-family: 'Inter', sans-serif;
  font-style: normal;
  font-weight: 600;
  font-size: 20px;
  line-height: 24px;
  border: none;
  /* color: #FFFFFF; */
  margin-right: 19px

}

.buy-now.women-pink{
    background-color: #720060;
    color: white;
}

.buy-now.men-blue{
    background-color: #002772;
    color: white;
}

.next-product{
  box-sizing: border-box;

  /* position: absolute; */
  min-width: 259px;
  min-height: 42px;
  left: 855px;
  top: 618px;

  /* background: #FFFFFF; */
  /* border: 3px solid #720060; */
  border-radius: 4px;
  font-family: 'Inter';
  font-style: normal;
  font-weight: 600;
  font-size: 20px;
  line-height: 24px;
  transition-duration: 0.4s;
  /* color: #720060; */

}

.next-product.women-pink{
    color: #720060;
    background-color: white;
    border: 3px solid #720060;
}

.next-product.men-blue{
    color: #002772;
    background-color: white;
    border: 3px solid #002772;
}

.next-product.women-pink:hover{
    background-color: #720060;
    color: white;
}

.next-product.men-blue:hover{
    background-color: #002772;
    color: white;
}

/* gambar produk */
.intersect{
    display: flex;
    justify-content: center;
    align-items: center;
  
}

/* .rectangle-7.unavailable{
    width: 1120px;
    height: 580px;
} */
.product-image{
    /* position: absolute;
    height: 45%;
    width: auto; */

    /* box-sizing: border-box; */

    position: absolute;
    /* width: 305.81px;
    height: 407px; */
    /* display: flex; */
    

    height:55%;
    width: auto; 
    /* left: 85px; */
    /* top: 100px; */

    /* float: center; */
    /* display: grid;
    justify-content: center;
    align-content: center; */
    /* background-color: black; */
} 

/* background */

.background{
  display:grid;
  grid-template-rows: 75% auto;

}

.background-men{
  background-color: #d6e6ff;
  
}

.background-women{
  background-color: #FDE2FF ;
  
}

.background .top-background{
  display: flex;
  /* background-color: #FDE2FF; */
  min-width: 150px;
  min-height: 548px;
  width: 100%;
  height: 80%;
  /* position:absolute; */
  /* z-index: -1; */
}

.background-misc{
    background-color: #D8D7D7;
}

.unavailable{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    
    
}

.unavailable button{
    box-sizing: border-box;

    /* position: absolute; */
    width: 465px;
    height: 42px;
    /* left: 431px; */
    margin: 4px;
    top: 409px;

    background: #FFFFFF;
    border: 3px solid #000000;
    border-radius: 4px;

    color: #3F3F3F;
    transition-duration: 0.4s;
}
.unavailable button:hover{
    background-color: #DCDCDC ;
    color:#000000;
}

/* loader */
.loading{
    /* height: 20px; */
    position:relative;
}

.loading input{
    position: absolute;
    width: 259px;
    height: 42px;
    opacity: 0;
    cursor:pointer;
    z-index:2;
    
}

 /* .loader {
  border: 16px solid #f3f3f3;
  border-radius: 50%;
  border-top: 16px solid blue;
  border-bottom: 16px solid blue;
  width: 120px;
  height: 120px;
  -webkit-animation: spin 2s linear infinite;
  animation: spin 2s linear infinite;
  right: 100px;
  display:flex;
}

@-webkit-keyframes spin {
  0% { -webkit-transform: rotate(0deg); }
  100% { -webkit-transform: rotate(360deg); }
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.no-loader{
    border: 16px solid #f3f3f3;
  border-radius: 50%;
  border-top: 16px solid blue;
  border-bottom: 16px solid blue;
  width: 120px;
  height: 120px;
  -webkit-animation: spin 2s linear infinite;
  animation: spin 2s linear infinite;
  right: 100px;
  
    display:none;
} */

/* media query */
@media only screen and (max-width:1280px){
    .intersect{
        width: 80%;
    }

    .rectangle-7{
        top: 50px;
    }
    .group-4{
        height: 60%;
    }
    .group-7{
        width:80%;
        
    }
    .product-image{
        height: 40%;
        width: auto;
    }
    .garis-pembatas{
        width: 100%;
    }

    .next-product{
        left: 0;
    }
}
</style>