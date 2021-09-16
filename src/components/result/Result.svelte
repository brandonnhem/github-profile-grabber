<script>
    import Bio from './Bio.svelte';
    import Stats from './Stats.svelte';
    import Links from './Links.svelte';

    import { userData } from '../stores';
    import { onDestroy, onMount } from 'svelte';

    let userData_values;
    let bioJSON, statsJSON, linksJSON = {};
    const monthNames = ["Jan", "Feb", "Mar", "Apr", "May", "Jun",
                        "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
    const unsubscribe = userData.subscribe(value => {
        userData_values = value;
        let dateObj = new Date(userData_values.created_at);
        let day = dateObj.getUTCDate();
        let month = dateObj.getMonth();
        let year = dateObj.getUTCFullYear();
        let newDate = `${day} ${monthNames[month]} ${year}`;
        bioJSON = {'avatar_url':userData_values.avatar_url, 'bio':userData_values.bio, 'created_at':newDate, 'login':userData_values.login, 'name':userData_values.name};
        statsJSON = {'public_repos':userData_values.public_repos, 'followers':userData_values.followers, 'following':userData_values.following};
        linksJSON = {'website':userData_values.blog, 'company':userData_values.company, 'location':userData_values.location, 'twitter_username':userData_values.twitter_username};
    });

	onDestroy(unsubscribe);

    let response = {};
    onMount(async () => {
        let promise = await fetch('https://api.github.com/users/octocat');
        response = await promise.json();
        let dateObj = new Date(response.created_at);
        let day = dateObj.getUTCDate();
        let month = dateObj.getMonth();
        let year = dateObj.getUTCFullYear();
        let newDate = `${day} ${monthNames[month]} ${year}`;
        bioJSON = {'avatar_url':response.avatar_url, 'bio':response.bio, 'created_at':newDate, 'login':response.login, 'name':response.name};
        statsJSON = {'public_repos':response.public_repos, 'followers':response.followers, 'following':response.following};
        linksJSON = {'website':response.blog, 'company':response.company, 'location':response.location, 'twitter_username':response.twitter_username};
    });

</script>

<section class="result">
    <Bio {...bioJSON}/>
    <Stats {...statsJSON}/>
    <Links {...linksJSON}/>
</section>

<style>
    .result {
        background-color: white;
        border-radius: 0.9375rem;
        padding: 1.5rem;
        margin-top: 3vh;
        -webkit-box-shadow: 0 0.25rem 0.25rem 0 rgba(0,0,0,0.25);
        -moz-box-shadow: 0 0.25rem 0.25rem 0 rgba(0,0,0,0.25);
        box-shadow: 0 0.25rem 0.25rem 0 rgba(0,0,0,0.25);
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