<script>
  export const prerender = true;

  import Instagram from "$components/helpers/faInstagram.svelte";
  import Twitter from "$components/helpers/faTwitter.svelte";
  import Facebook from "$components/helpers/faFacebookSquare.svelte";

  const links = [
    { name: "contact", url: "mailto:csgs@ashoka.ac.in" },
    { name: "twitter", url: "https://twitter.com/csgs_ashoka/" },
    { name: "facebook", url: "https://facebook.com/csgsashoka" },
    { name: "instagram", url: "https://instagram.com/csgs_ashoka/" }
  ];
</script>

<footer>
  <div >
    <a href="https://csgs.ashoka.edu.in/"><img preload src="/images/logo.png" alt="CSGS Logo" /></a>
  </div>

  <p class="description text-center  text-[14px] font-sans   text-white  ">
    The Centre for Studies in Gender and Sexuality (CSGS) is the first Centre of its kind in India
    to study the broader spectrum of questions relating to both gender and sexuality.
  </p>
  <div class="flex text-white gap-4 flex-col py-4 px-10">
    <p class="font-bold uppercase">Connect with us</p>
    <div class="flex flex-row gap-4 justify-center items-center">
      {#each links as link}
        <a href={link.url} ref="external">
          {#if link.name === "twitter"}
            <Twitter />
          {:else if link.name === "facebook"}
            <Facebook />
          {:else if link.name === "instagram"}
            <Instagram />
          {/if}
        </a>
      {/each}
    </div>
  </div>
</footer>

<style>
  footer {
    width: 100vw !important;
    background-color: #0d3862;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    padding: 2rem 0;
  }

  footer img {
    width: 100%;
    height: auto;
  }

  .description {
    font-size: 16px;
    line-height: 1.5;
    color: #fff;
    width: 30%;
  }

  @media (max-width: 768px) {
    footer {
      flex-direction: column;
      padding: 2rem 0;
    }
  }
</style>
