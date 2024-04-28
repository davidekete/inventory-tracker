<script>
    import {Link} from "svelte-routing";
    import Card from './Card.svelte';
    import { onMount } from 'svelte'
    import Parse from 'parse/dist/parse.min.js';

    let products = [];

    const fetchProducts = async () => {
      try {
        const query = new Parse.Query("Inventory");
        const productsData = await query.find();
        products = productsData;
      } catch (error) {
        console.log(error);
      }
    };

    onMount(fetchProducts);

    const deleteProduct = async (id) => {
      try {
        const Product = Parse.Object.extend("Inventory");
        const product = new Product();
        product.id = id;
        await product.destroy();
        const newData = products.filter((item) => item.id !== id);
        products = newData;
      } catch (error) {
        console.log(error);
      }
    };
</script>

<main>
    <p>A way to manage and keep track of products in your inventory</p>
    <Link to="/add-products" class="link">Add Products here &#x2192;</Link>

    <div class="products">
      {#each products as product}
	      <Card 
        name={product.get('name')} 
        quantity={product.get('quantity')} 
        price={product.get('price')}
        handleClick={() => deleteProduct(product.id)}
        />
	    {/each}
    </div>
</main>

<style>
    main{
    display: flex;
    flex-direction: column;
    gap: 2rem;
    align-items: center;
  }

  .products{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 3rem;
    border-top: 2px solid #e2e2e2;
    margin-block-start: 3rem;
    padding-block-start: 2rem;
  }

</style>
