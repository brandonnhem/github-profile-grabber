<script>
    import Bio from './Bio.svelte';
    import Stats from './Stats.svelte';
    import Links from './Links.svelte';
    import { Octokit } from "@octokit/rest";

    const octokit = new Octokit({
        auth: API_KEY,
        userAgent: 'devfinder v.1',
    });


    // TODO: create GET method

    // myAsyncMethod();

    // async function myAsyncMethod() {
    //     const result = await octokit.request('GET /users/{username}', {
    //         username: 'brandonnhem'
    //     });
    //     console.log(result);
    // }
</script>

<section class="result">
    <Bio />
    <Stats />
    <Links />
</section>

<style>
    .result {
        background-color: white;
        border-radius: 15px;
        padding: 1.5rem;
        margin-top: 3vh;
        -webkit-box-shadow: 0 4px 4px 0 rgba(0,0,0,0.25);
        -moz-box-shadow: 0 4px 4px 0 rgba(0,0,0,0.25);
        box-shadow: 0 4px 4px 0 rgba(0,0,0,0.25);
    }

    @media only screen and (min-width: 768px) {
        .result {
            padding: 3rem;
        }
    }

    @media only screen and (min-width: 1440px) {
        .result {
            padding: 2rem 4rem;
        }
    }

    @media (prefers-color-scheme: dark) {
        :global(body:not(.light)) .result {
            background-color: hsl(222, 41%, 20%);
            -webkit-box-shadow: 0 0 0 0 rgba(0,0,0,0);
            -moz-box-shadow: 0 0 0 0 rgba(0,0,0,0);
            box-shadow: 0 0 0 0 rgba(0,0,0,0);
        }
    }
</style>