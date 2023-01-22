<script>
  export let title = "Qurbatein: Issue 1";
  export let description = "A non-profit gender and sexuality bi-annual by the Centre for Studies in Gender and Sexuality (CSGS) at Ashoka University";
  export let url = "https://csgs.ashoka.edu.in/";
  export let author = "CSGS";
  export let date = "2021-09-01";
  export let share =  "assets/social.png";
  export let isPost = false;
  export let slug = "";
  export let category = "";
  
  if(slug && isPost)
  {
    url = "https://csgs.ashoka.edu.in/" + category +  "/" + slug;
  }

  let jsonSchema = {
    "@context": "https://schema.org",
    "@type": "Article",
    "mainEntityOfPage": {
      "@type": "WebPage",
      "@id": url
    },
    "headline": title,
    "description": description,
    "image": {
      "@type": "ImageObject",
      "url": share
    },
    "author": {
      "@type": "Person",
      "name": author
    },
    "publisher": {
      "@type": "Organization",
      "name": "Centre for Sexuality and Gender Studies",
    },
    "datePublished": date,
    "dateModified": date
  }

  let jsonSchemaString = JSON.stringify(jsonSchema);
  console.log(jsonSchemaString);
</script>

<svelte:head>
  <title>{title}</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;0,700;1,300;1,400;1,500;1,600;1,700&family=DM+Serif+Display:ital@0;1&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=block" rel="stylesheet"> 
<meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <meta name="description" content={description} />
  <meta name="author" content="Centre for Studies in Gender and Sexuality" />
  <meta name="news_keywords" content="" />

  <meta property="og:title" content={title} />
  <meta property="og:site_name" content="Qurbatein by CSGS" />
  <meta property="og:url" content={url} />
  <meta property="og:description" content={description} />
  <meta property="og:type" content="article" />
  <meta property="og:locale" content="en_US" />

  <meta property="og:image" content="https://csgs-qurbatein.netlify.app/{share}" />
  <meta property="og:image:type" content="image/jpeg" />
  <meta property="og:image:width" content="1200" />
  <meta property="og:image:height" content="600" />

  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:site" content="https://csgs.ashoka.edu.in/" />
  <meta name="twitter:creator" content="@csgs_ashoka" />
  <meta name="twitter:title" content={title} />
  <meta name="twitter:description" content={description} />
  <meta name="twitter:image:src" content="https://csgs-qurbatein.netlify.app/{share}" />

  <meta name="robots" content="max-image-preview:large" />

  <link rel="canonical" href="{url}/" />
  <script src="https://unpkg.com/flowbite@1.5.1/dist/flowbite.js"></script>

  {#if isPost}
  {@html `<script type="application/ld+json">${jsonSchemaString}</script>`}
  {/if}
  
</svelte:head>
