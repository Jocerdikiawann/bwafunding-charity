<script>
  import router from "page";
  import Home from "./pages/Home.svelte";
  import About from "./pages/About.svelte";
  import Contact from "./pages/Contact.svelte";
  import Donation from "./pages/Donation.svelte";
  import Notfound from "./pages/Notfound.svelte";
  import Success from "./pages/Succes.svelte";
import Succes from "./pages/Succes.svelte";

  let page, params;

  // byte code di cek dari yang paling atas dan bergilir 
  router("/", () => (page = Home));
  router("/about", () => (page = About));
  router("/contact", () => (page = Contact));
  router("/success", ()=> (page = Succes));
  router(
    "/donation/:id",
    (ctx, next) => {
      params = ctx.params;
      next();
    },
    () => (page = Donation)
  );
    //elsenya ini diluar
  router('/*', ()=> (page = Notfound));

  router.start();
</script>

<svelte:component this={page} {params} />
