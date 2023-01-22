<script context="module">
export const prerender = true;
	import "/src/styles/tailwind.css";
	import content from "$data/content.csv";
      const stories = content;
	export async function load({ page }) {
		try {
			const post = await import(`../../data/posts/${page.params.photoEssay}.json`);
			// Filter stories by slug
			const story = stories.filter(story => story.slug === page.params.photoEssay)[0];
			// Combine data
			const data = { ...post, ...story };
			return {
				// Data passed into svelte component
				props: {
					post: data
				}
			};
		} catch (e) {
			return {
				props: {
					post: {
						title: "404",
						content: "Page not found"
					}
				}
			};
		}
	}
</script>
<script>
    import BodyText from "$components/Blocks/BodyText.svelte";
    import ArticleImage from "$components/Blocks/ArticleImage.svelte";
    import Pullquote from "$components/Blocks/Pullquote.svelte";
    import EssayPhoto from "$components/Blocks/EssayPhoto.svelte";
    import Bio from "$components/Blocks/Bio.svelte";
    import Footnotes from "$components/Blocks/Footnotes.svelte";
    import Endnotes from "$components/Blocks/Endnotes.svelte";
    export let post;
    // Convert comma separated string to array
    let authors = post.author.split(',');
    authors = authors.map(string => string.trim())
  // Find block of type 'Bio' in the blocks array in post
  const bio = post.blocks.filter(block => block.Type === 'Bio')[0];
  let authorPhotos = [];
  if (bio) {
    if (bio.photo.includes(',')) {
      authorPhotos = bio.photo.split(',');
      authorPhotos = authorPhotos.map(string => string.trim())
      bio.photo = authorPhotos;
    } else {
      bio.photo = bio.photo.trim();
    }
  }

</script>
{#if post.title != "404"}
<main>
<section class="mx-auto container pt-12 pb-6">
<div class="top mx-auto">
    <img src="/assets/header.png" class="mx-auto pb-6" width="250" alt={post.title} />
    <h1 class="font-dm text-5xl px-4 text-center italic leading-royal font-extrabold text-[color:var(--color-text)]">{post.title}</h1>
    <hr class="border-b-[1px] my-6 border-[color:var(--color-text)] w-[50px] mx-auto" />
    <h2 class="pb-6 font-libre tracking-wide text-center text-xl">{post.author}</h2>
    {#if post.additionalAuthors}
    <h2 class="pb-6 font-libre tracking-wide w-1/2 mx-auto leading-6 text-center text-sm">{post.additionalAuthors}</h2>
    {/if}
</div>

</section>

<section class="mx-auto  px-6">

   {#each post.blocks as block}
   {#if block.Type == "Text"}
         <section class="lg:w-2/3 py-2 lg:py-8 mx-auto">
             <BodyText  align={block.Direction} text={block.Text}/>
         </section>
    {/if}

    {#if block.Type == "ArticleImage"}
        <ArticleImage src={block.Link} caption={block.caption}/>
    {/if}

    {#if block.Type == "pullquote"}
       <Pullquote text={block.Text} attribution={block.attribution}/>
    {/if}


    {#if block.Type == "EssayPhoto"}
        <EssayPhoto src={block.src} caption={block.caption}/>
    {/if}



    {#if block.Type == "h2"}
    <section class="lg:w-2/3 py-2 mx-auto">

     <h2> {block.Text}</h2>
    </section>

    {/if}

    {#if block.Type == "h4"}
    <section class="lg:w-2/3 py-2 mx-auto">

     <h4> {block.Text}</h4>
    </section>
    {/if}

    

    {/each}

    <section class="mx-auto lg:w-2/3">
    {#if post.endnotes}
        <Endnotes text={post.endnotes} />
     {/if}
    </section>
    <section class="mx-auto lg:w-2/3">
    {#if post.references}
        <Footnotes text={post.references} />
     {/if}
    </section>

    {#each post.blocks as block}
        {#if block.Type == "Bio"}
            <Bio text={block.Text} name={authors} image={authorPhotos}/>
        {/if}
    {/each}
</main>
{:else}
<main>
<section class="mx-auto container w-4/5 pt-24 pb-6">
    Page not found
</section>
</main>
{/if}


<style>
    h4 {
        font-family: 'DM Serif Display', serif;
        font-size: 1.5rem;
        font-weight: 400;
        line-height: 1.5;
        color: var(--color-text);
    }
</style>
