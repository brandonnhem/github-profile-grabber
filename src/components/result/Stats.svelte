<div class="stats">
    <div class="stats-col">
        <p>Repos</p>
        <h3>8</h3>
    </div>
    <div class="stats-col">
        <p>Followers</p>
        <h3>3938</h3>
    </div>
    <div class="stats-col">
        <p>Following</p>
        <h3>9</h3>
    </div>
</div>

<style>
    .stats {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-evenly;
        background-color: hsl(227, 100%, 98%);
        border-radius: 15px;
    }

    .stats-col {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 0;
    }

    p {
        font-size: 11px;
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
            font-size: 13px;
        }

        h3 {
            font-size: 22px;
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
</style>