<script>
  import Parse from 'parse/dist/parse.min.js';
  import './styles/global.css'
  import {Route, Router} from "svelte-routing";
  import AddProduct from './AddProduct.svelte';
  import Home from './Home.svelte';

  Parse.initialize("YOUR_APP_ID", "YOUR_JAVASCRIPT_KEY");
  Parse.serverURL = "https://parseapi.back4app.com/";

  export let url = "";
</script>

<Router {url}>
  <h1>Inventory Tracker</h1>
  
  <div class="container">
    <Route path="/" component={Home} />
    <Route path="/add-products" component={AddProduct} /> 
  </div>
</Router>


<style>

  h1{
    text-align: center;
    font-family: "Poppins", sans-serif;
    margin-block-start: 1rem;
    margin-block-end: 6rem;
  }

</style>
