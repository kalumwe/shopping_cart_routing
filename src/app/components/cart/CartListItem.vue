    <template>
      <div class="box">
        <div class="cart-item__details">
          <p class="is-inline">{{ cartItem.title }}</p>
          <br>
          <img :src="getImageUrl(cartItem.imageUrl)" alt="Product Image" class="product-image m-2">
          <div>
            <span class="cart-item--price has-text-primary has-text-weight-bold">
             {{ cartItem.price }}$ x {{ cartItem.quantity }}
            </span>
            <span>
             <i @click="addCartItem(cartItem)"
              class="fa fa-arrow-circle-up cart-item__modify"></i>
             <i @click="removeCartItem(cartItem)"
              class="fa fa-arrow-circle-down cart-item__modify"></i>
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
.cart-item--modify {
  cursor: pointer;
  margin: 0 1px;
}
.product-image {
    width: 74px; 
    height: auto;
 }
</style>