<div class="bio">
    <div class="bio-header">
        <div class="profile-pic">
            <img src="https://avatars.githubusercontent.com/u/583231?v=4" alt="profile">
        </div>
        <div class="profile-info">
            <h3 id="username">USERNAME</h3>
            <h4 id="handle"><a href="/">@HANDLE</a></h4>
            <h4 id="date">Joined 9 Sep 2021</h4>
        </div>
    </div>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Adipisci, facere magni maiores totam, ea repellat eveniet, corrupti tempora.</p>
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
        width: 70px;
        height: 70px;
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
            height: 117px;
            width: 117px;
        }

        h3 {
            font-size: 26px;
            margin-bottom: 1vh;
        }

        h4 {
            font-size: 16px;
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
</style>