<script>
  import content from "$data/content.csv"
  import star from "$svg/star.svg"
  // Keep only content that has category "Poetry"
  const poetry = content.filter(item => item.category === "poetry")
  
</script>

<section  id="poetry" class="grid min-h-[50vh] py-12 lg:py-28 max-w-9xl mx-auto px-4 lg:grid-cols-8 gap-8 justify-end items-start">
  
    <div class="col-span-3 content  flex justify-center items-center h-full">
        <h2 class="text-7xl font-cormorant  font-bold  leading-10 tracking-tight text-left text-[color:var(--color-background)] px-6 lg:px-0  sm:leading-none md:text-6xl lg:text-[10rem]">Poetry</h2>
    </div>
    <div class=" col-span-5 content flex items-center ">
        <div class="flex-1 max-w-4xl mx-auto p-8">
          <ul class="grid grid-cols-6 gap-8">
            <a class="col-span-6 md:col-span-2 border-2 bg-[color:var(--color-background)] border-black hover-content" href="/poetry/{poetry[0].slug}">
            <li class="min-h-64">
                <div class="p-6">
                  {#if poetry[0].featured == "TRUE"}
                  <div class="flex py-1 justify-center items-center">{@html star} <span class="text-[color:#eac638] px-2 font-bold uppercase"> </span></div>
                  {/if}
                  <h3 class="font-libre italic text-center font-bold text-2xl">{poetry[0].title}</h3>
                  <hr class="divider">
                  <p class="text-center text-xl leading-10 tracking-tight text-[color:var(--color-text)] md:text-center sm:leading-none md:text-6xl lg:text-[1.5rem]">{poetry[0].author}</p>
                </div>
              </li>
            </a>
            <a  class="col-span-6 md:col-span-4 border-2 bg-[color:var(--color-primary)] md:h-full h-44 hover:border-2 hover-content" href="/poetry/{poetry[1].slug}" >
            <li class="min-h-56">
              <div class="p-6 mt-0 md:mt-6 text-white">
                {#if poetry[1].featured == "TRUE"}
                  <div class="flex py-1 justify-center items-center">{@html star} <span class="text-[color:#eac638] px-2 font-bold uppercase"> </span></div>
                  {/if}
                <h3 class="font-mono text-center font-semibold text-2xl">{poetry[1].title}</h3>
                <hr class="divider-white ">
                <p class="text-center text-xl leading-10 tracking-tight text-white md:text-center sm:leading-none md:text-6xl lg:text-[1.5rem]">{poetry[1].author}</p>
              </div>
             </li>
            </a>
           
            <a class="col-span-6 md:col-span-6 border-2 bg-[color:var(--color-background)] border-black hover-content" href="/poetry/{poetry[2].slug}">
            <li class="min-h-64">
                <div class="p-6">
                  {#if poetry[2].featured == "TRUE"}
                  <div class="flex py-1 justify-center items-center">{@html star} <span class="text-[color:#eac638] px-2 font-bold uppercase"> </span></div>
                  {/if}
                  <h3 class="font-libre italic text-center font-bold text-2xl">{poetry[2].title}</h3>
                  <hr class="divider">
                  <p class="text-center text-xl leading-10 tracking-tight text-[color:var(--color-text)] md:text-center sm:leading-none md:text-6xl lg:text-[1.5rem]">{poetry[2].author}</p>
                </div>
              </li>
            </a>
            </ul>
        </div>
      </div>
</section>

<style>

  #poetry {
    position: relative;

  }

#poetry::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("/images/issue_2_4.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  z-index: -1;

  /* Sticky scroll */

  background-attachment: fixed;
  filter: brightness(0.5) sepia(0.5) saturate(0.5) ;
}



h2 {
  color: var(--color-background);
}
</style>
