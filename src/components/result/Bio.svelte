<script>
    export let avatar_url;
    export let bio;
    export let created_at;
    export let login;
    export let name;
</script>

<div class="bio">
    <div class="bio-header">
        <div class="profile-pic">
            <img src="{avatar_url}" alt="profile">
        </div>
        <div class="profile-info">
            {#if (name === null)}
                <h3 id="username">{login}</h3>
            {:else}
                <h3 id="username">{name}</h3>
            {/if}
            <h4 id="handle"><a href="https://github.com/{login}">@{login}</a></h4>
            <h4 id="date">Joined {created_at}</h4>
        </div>
    </div>
    {#if (bio === null)}
        <p>This profile has no bio.</p>
    {:else}
        <p>{bio}</p>
    {/if}
</div>

<style>
    p {
        color:hsl(217, 35%, 45%);
    }

    .bio-header {
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    img {
        width: 4.375rem;
        height: 4.375rem;
        border-radius: 50%;
    }

    .profile-info {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        margin-left: 5vw;
    }

    h3 {
        font-weight: 700;
        margin: 0;
    }

    h4 {
        margin: 0;
        color: hsl(217, 20%, 51%);
    }

    a {
        color: hsl(212, 100%, 50%);
        text-decoration: none;
    }

    @media only screen and (min-width: 768px) {
        img {
            height: 7.3125rem;
            width: 7.3125rem;
        }

        h3 {
            font-size: 1.625rem;
            margin-bottom: 1vh;
        }

        h4 {
            font-size: 1rem;
        }
    }
    
    @media only screen and (min-width: 1440px) {
        .profile-info {
            position: relative;
        }

        #username {
            position: absolute;
            top: -5vh;
            left: -2vw;
            width: max-content;
        }

        #handle {
            position: absolute;
            top: -1vh;
            left: -2vw;
        }

        #date {
            position: absolute;
            top: -5vh;
            left: 20vw;
            width: max-content;
        }

        p {
            margin-left: 11vw;
            margin-top: -2vw;
        }
    }

    @media only screen and (min-width: 1600px) {
        #username, #handle {
            left: -1vw;
        }

        #date {
            left: 29vw;
        }
    }

    @media (prefers-color-scheme: dark) {
        :global(body:not(.light)) h4, p {
            color: hsl(0, 0%, 100%);
        }

        :global(body:not(.dark)) p {
            color:hsl(217, 35%, 45%);
        }
    }
</style>