<script>
    import content from "$data/content.csv"
    import star from "$svg/star.svg"
    // Keep only content that has category "article"
    const article = content.filter(item => item.category === "articles")
  </script>
  
  <section class="lg:grid lg:min-h-[50vh] max-w-9xl mx-auto mb-12 md:mb-0 lg:grid-cols-8 gap-8 justify-end items-start">
      <div id="articles" class="col-span-3 flex h-40 justify-center items-center md:h-full">
          <h2 class="font-cormorant  font-bold  px-8 leading-10 tracking-tight text-left text-[color:var(--color-background)] md:text-left sm:leading-none text-6xl md:text-6xl lg:text-[9rem]">Articles</h2>
      </div>
      <div class=" col-span-5 flex items-center ">
          <div class="flex-1 max-w-4xl mx-auto p-8">
            <ul class="grid grid-cols-6 gap-4">
                {#each article as item, i}

                <li class="col-span-6 border-t-[3px] lg:my-4 border-black">
                    <a href="/articles/{item.slug}" class="block hover:text-[color:var(--color-text)]">

                    <div class="md:flex flex-col md:flex-row py-4 justify-start items-start gap-6">
                        <div class="flex-0">
                            <span class="text-xl"><span class="font-bold">[</span>{i + 1}<span class="font-bold"> ]</span>
                        </div>
                        <div class="flex-1">
                                <h3 class="lg:text-2xl text-xl font-mono hover:underline hover:cursor-pointer ">{item.title}</h3>
                        </div>
                       
                        <div class="flex justify-end md:py-0 py-2 flex-col md:items-end items-start">
                            <span class="text-sm font-mono">{item.author}</span>
                            {#if item.featured == "TRUE"}
                            <div class="flex py-2  justify-start items-center">{@html star}</div>
                            {/if}
                        </div>
                    </div>
                    </a>
                </li>
                {/each}
            </ul>
          </div>
        </div>
  </section>
  
  <style>
    #articles {
   position: relative;
    }  

    #articles::before {
   
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    background-image: url('/images/issue_2_3.jpg');
    background-size: cover;
    
    
    /* Background zoom to left  */
    background-position: 20% 40%;

    background-repeat: no-repeat;
    background-origin: border-box;
    filter: grayscale(0.1) sepia(0.2) contrast(1.2) brightness(0.6);
    }
  </style>
  