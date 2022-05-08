<script>
    const news_api = "a871285be1c82d72f5215d2717db1c1c";
    export let keyword;
    let URL = `https://gnews.io/api/v4/search?q=${keyword}&token=${news_api}`;
    let articles = [];

    $: fetch(URL)
		.then(r => r.json())
		.then(data => {
			articles = data["articles"];
			window.scrollTo(0, 0);
		});
</script>

<p class="about"> *You can filter news with news/[keywords].
</p>

<div class="container">

        {#each articles as article}
            <div class="card">
                <img src="{article.image}" alt="">
                <div class="card-body">
                    <h3>{article.title}</h3>
                    <p> {article.description} </p>
                    <a href="{article.url}">Full story ></a>
                </div>
            </div>
        {/each}

</div>

<style>
    a {
	    text-decoration: underline;
    }

    .about {
        font-style: italic;
        padding-bottom: 2%;
        text-align: center;
    }

    h3 {
        padding-top: 1%;
        text-align: center;
        font-weight: bold;
    }

    .container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(305px, 1fr));
        grid-gap: 15px;
    }
    
    .container > .card img {
        margin-left: auto;
        margin-right: auto;
        max-width: 90%;
    }
    .card > .card-body {
        max-width: 90%;
        margin-left: auto;
        margin-right: auto;
    }
    </style>
    