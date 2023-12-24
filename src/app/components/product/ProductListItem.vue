    <template>   
       <div>
        <img :src="getImageUrl(productItem.imageUrl)" alt="Product Image" class="product-image">
            <h2 class="has-text-weight-bold">{{ productItem.title }}
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
            width: 164px; 
            height: auto;
        }
    </style>