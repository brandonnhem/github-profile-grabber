<script>
    import { userData } from './stores.js';
    let username;
    let userObject;
    function submit(e) {
        e.preventDefault();
        fetchUser(username);
    }

    async function fetchUser(user) {
        try {
            let promise = await fetch("https://api.github.com/users/" + user);
            
            if(promise.ok) {
                userObject = await promise.json();
                userData.update(() => userObject);
            } else {
                document.getElementById('error').style.display = 'block';
                if (document.documentElement.clientWidth >= 768 && document.documentElement.clientWidth < 1024) {
                    document.getElementById('text-box').style.width = '45vw';
                } else if (document.documentElement.clientWidth >= 1024 && document.documentElement.clientWidth < 1440) {
                    document.getElementById('text-box').style.width = '55vw';
                } else if (document.documentElement.clientWidth >= 1440 && document.documentElement.clientWidth < 1600) {
                    document.getElementById('text-box').style.width = '32vw';
                } else if (document.documentElement.clientWidth >= 1600) {
                    document.getElementById('text-box').style.width = '40vw';
                } else {
                    document.getElementById('text-box').style.width = '25vw';
                }
                document.getElementById('search-btn').style.marginLeft = '2vw';
            }
        } catch (err) {
            return console.log(err);
        }
    }

    function reset() {
        if (document.getElementById('error').style.display === 'block') {
            document.getElementById('error').style.display = 'none';
            document.getElementById('text-box').style.width = '50vw';
            document.getElementById('search-btn').style.marginLeft = '0';
            if (username !== '') {
                username = '';
            }
        }
    }
</script>

<form class="search-bar" action="GET">
    <div class="sub-search" on:click="{reset}">
        <svg height="24" width="25" xmlns="http://www.w3.org/2000/svg"><path d="M10.609 0c5.85 0 10.608 4.746 10.608 10.58 0 2.609-.952 5-2.527 6.847l5.112 5.087a.87.87 0 01-1.227 1.233l-5.118-5.093a10.58 10.58 0 01-6.848 2.505C4.759 21.16 0 16.413 0 10.58 0 4.747 4.76 0 10.609 0zm0 1.74c-4.891 0-8.87 3.965-8.87 8.84 0 4.874 3.979 8.84 8.87 8.84a8.855 8.855 0 006.213-2.537l.04-.047a.881.881 0 01.058-.053 8.786 8.786 0 002.558-6.203c0-4.875-3.979-8.84-8.87-8.84z" fill="#0079ff"/></svg>
        <input type="text" placeholder="Search GitHub username..." bind:value="{username}" id="text-box">
        <div class="error-message" id="error">No results</div>
    </div>
    <button type="submit" on:click="{submit}" id="search-btn">Search</button>
</form>

<style>
    .error-message {
        color: red;
        font-size: 0.75rem;
        width: max-content;
        display: none;
    }

    .search-bar {
        background-color: white;
        border-radius: 0.9375rem;
        height: 3.75rem;
        display: flex;
        flex-direction: row;
        align-items: center;
        padding: 0 3vw;
        justify-content: space-around;
        -webkit-box-shadow: 0 0.25rem 0.25rem 0 rgba(0,0,0,0.25);
        -moz-box-shadow: 0 0.25rem 0.25rem 0 rgba(0,0,0,0.25);
        box-shadow: 0 0.25rem 0.25rem 0 rgba(0,0,0,0.25);
    }

    .sub-search {
        display: flex;
        align-items: center;
    }

    button {
        background-color: hsl(212, 100%, 50%);
        color: white;
        border-radius: 0.625rem;
        height: 2.875rem;
        width: 5.25rem;
        border: none;
        font-weight: 700;
        cursor: pointer;
    }

    button:hover {
        background-color: hsl(212, 100%, 69%);
    }

    input {
        border: none;
        font-size: 0.75rem;
        width: 50vw;
        margin-left: 1vw;
        caret-color: hsl(212, 100%, 50%);
        cursor: pointer;
    }

    input:focus {
        outline: none;
    }

    @media only screen and (min-width: 768px) {
        .search-bar {
            justify-content: space-between;
            padding-right: 1.5vw;
        }

        button {
            font-size: 1rem;
            width: 6.625rem;
            height: 3.125rem;
        }

        input {
            font-size: 1.25rem;
        }
    }

    @media only screen and (min-width: 1440px) {
        input {
            width: 33vw;
        }
    }

    @media (prefers-color-scheme: dark) {
        :global(body:not(.light)) .search-bar {
            background-color: hsl(222, 41%, 20%);
            -webkit-box-shadow: 0 0 0 0 rgba(0,0,0,0);
            -moz-box-shadow: 0 0 0 0 rgba(0,0,0,0);
            box-shadow: 0 0 0 0 rgba(0,0,0,0);
        }

        :global(body:not(.light)) input {
            background-color: hsl(222, 41%, 20%);
            color: hsl(0, 0%, 100%);
        }

        :global(body:not(.light)) ::placeholder {
            color: hsl(0, 0%, 100%);
        }
    }
</style>