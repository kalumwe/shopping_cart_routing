    <template>   
       <div>
         <router-link
            :to="'/products/' + productItem.id">       
           <img :src="require('../../assets/' + productItem.imageUrl)" class="product-image my-2 rounded" />
        </router-link>
            <h2 class="has-text-weight-bold">
                <router-link
                  :to="'/products/' + productItem.id">
                  {{ productItem.title }}
                </router-link>
              <span @click="addCartItem(productItem)"
                     class="tag is-primary is-pulled-right has-text-white">
               Add to Cart
              </span>
            </h2>
            <p>{{ productItem.description }}</p>
            <span class="has-text-primary has-text-weight-bold">
                <i class="fa fa-usd"></i> {{ productItem.price }}
            </span>
        </div>
    </template>

    <script>
    import { mapActions } from 'vuex';

        export default {
           name: 'ProductListItem',
           props: ['productItem'],
           methods: {
               ...mapActions([
                    'addCartItem'
               ]),
               getImageUrl(imagePath) {
                  return `/img/${imagePath}`; 
               },
           }
        }
    </script>


    <style scoped>
       .tag {
           cursor: pointer;
        }
        .product-image {
            width: 184px; 
            height: auto;
        }
    </style>