<script>
    export let public_repos;
    export let followers;
    export let following;
</script>

<div class="stats">
    <div class="stats-col">
        <p>Repos</p>
        <h3>{public_repos}</h3>
    </div>
    <div class="stats-col">
        <p>Followers</p>
        <h3>{followers}</h3>
    </div>
    <div class="stats-col">
        <p>Following</p>
        <h3>{following}</h3>
    </div>
</div>

<style>
    .stats {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-evenly;
        background-color: hsl(227, 100%, 98%);
        border-radius: 0.9375rem;
    }

    .stats-col {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0;
    }

    p {
        font-size: 0.6875rem;
        color:hsl(217, 35%, 45%);
        padding-top: 1rem;
    }

    h3 {
        font-weight: 700;
        padding-bottom: 1rem;
    }

    p, h3 {
        margin: 0;
    }

    @media only screen and (min-width: 768px) {
        p {
            font-size: 0.8125rem;
        }

        h3 {
            font-size: 1.375rem;
        }

        .stats {
            justify-content: space-around;
        }

        .stats-col {
            align-items: flex-start;
        }
    }
    
    @media only screen and (min-width: 1440px) {
        .stats {
            margin-left: 11vw;
        }
    }

    @media (prefers-color-scheme: dark) {
        :global(body:not(.light)) .stats {
            background-color: hsl(220, 40%, 13%);
        }

        :global(body:not(.light)) h3, p {
            color: hsl(0, 0%, 100%);
        }

        :global(body:not(.dark)) p {
            color:hsl(217, 35%, 45%);
        }
    }
</style>