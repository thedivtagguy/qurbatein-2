<script>
  import "$styles/app.css";
  import "flowbite/dist/flowbite.css";
  import Footer from "$components/Footer.svelte";
  export const router = true;
</script>

<main class="max-w-9xl mx-auto" id="content">
  <slot />
</main>
