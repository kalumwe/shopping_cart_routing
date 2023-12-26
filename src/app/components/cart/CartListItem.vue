    <template>
      <div class="box mx-auto">
        <div class="cart-item__details mx-auto ">
          <p class="is-inline">{{ cartItem.title }}</p>
          <br>
          <div 
             class="cart-item__image">
            <router-link
              :to="'/products/' + cartItem.id">
              <img :src="require('../../assets/' + cartItem.imageUrl)" class="product-image my-2 rounded"/>
            </router-link>
          </div>
          <div>
            <span class="cart-item--price has-text-primary has-text-weight-bold">
             {{ cartItem.price }}$ x {{ cartItem.quantity }}
            </span>
            <span>
             <i @click="addCartItem(cartItem)"
              class="fa fa-arrow-circle-up cart-item-modify"></i>
             <i @click="removeCartItem(cartItem)"
              class="fa fa-arrow-circle-down cart-item-modify"></i>
            </span>
          </div>
        </div>
      </div>
    </template>


<script>
import { mapActions } from 'vuex';

  export default {
    name: 'CartListItem',
    props: ['cartItem'],
    computed: {
     
   },
    methods: {
      ...mapActions([
        'addCartItem',
        'removeCartItem',
      ]),
      getImageUrl(imagePath) {
        return `img/${imagePath}`; 
      },  
    }
  };
</script>


<style scoped>
.cart-item-modify {
  cursor: pointer;
  margin: 0 1px;
}
.product-image {
    width: 144px; 
    height: auto;
 }

</style>