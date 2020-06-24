<script>
    import { v4 as uuidv4 } from 'uuid'

    import Players from '../components/create/Players.svelte'
    import Matches from '../components/create/Matches.svelte'

    import { players } from '../store.js'
    let rounds = 1
    // let players = []
    let matches = []

    // const addPlayer = () => {
    //     players = [...players, { id: uuidv4(), name: '', squad: [] }]
    // }

    // const generateMatches = () => {
    //     if (players.length >= 2) {
    //         for (let i = 0; i < rounds; i++) {
    //             players.forEach(player1 => {
    //                 players.forEach(player2 => {
    //                     if (player1 !== player2) {
    //                         matches = [
    //                             ...matches,
    //                             {
    //                                 player1: { ...player1 },
    //                                 player2: { ...player2 },
    //                             },
    //                         ]
    //                     }
    //                 })
    //             })
    //         }
    //     }
    // }

    // const finishMatch = match => {
    //     const player1 = players.find(player => player.id === match.player1.id)
    //     const player2 = players.find(player => player.id === match.player2.id)

    //     if (match.player1.score >= 0 && match.player2.score >= 0) {
    //         match.finished = true
    //         matches = matches

    //         if (match.player1.score > match.player2.score) {
    //             // Player 1 win
    //             player1.pts = (player1.pts || 0) + 3
    //         } else if (match.player2.score > match.player1.score) {
    //             // Player 2 win
    //             player2.pts = (player2.pts || 0) + 3
    //         } else {
    //             // draw
    //             player1.pts = (player1.pts || 0) + 1
    //             player2.pts = (player2.pts || 0) + 1
    //         }

    //         player1.gf = (player1.gf || 0) + match.player1.score
    //         player2.gf = (player2.gf || 0) + match.player2.score
    //         player1.ga = (player1.ga || 0) + match.player2.score
    //         player2.ga = (player2.ga || 0) + match.player1.score
    //         player1.gd =
    //             (player1.gd || 0) + match.player1.score - match.player2.score
    //         player2.gd =
    //             (player2.gd || 0) + match.player2.score - match.player1.score

    //         players = players
    //     }
    // }

    // const reset = () => {
    //     rounds = 1
    //     players = []
    //     matches = []
    // }
</script>

<!-- <form on:submit|preventDefault={generateMatches}> -->
<!-- <div>
        <label for="noOfRounds">Rounds</label>
        <input
            id="noOfRounds"
            type="number"
            min={1}
            bind:value={rounds}
            required />
    </div> -->

<!-- <div>
        {#each players as player, i}
            <input
                placeholder={`Player ${i + 1}`}
                bind:value={player.name}
                required />
        {/each}
        <button type="button" on:click={addPlayer}>Add Player</button>
    </div> -->
<Players />
<Matches />

<!-- <button type="submit">Generate Matches</button> -->
<!-- </form> -->

<div>
    <h1>Players</h1>
    <ul>
        {#each $players as player, i}
            <li>
                {player.name} -
                <strong>Squad:</strong>
                {#each player.squad as squadMember, i}
                    <span>{squadMember.name}</span>
                {/each}
            </li>
        {/each}
    </ul>
</div>

<!-- <div>
    <h1>Matches</h1>
    <ol>
        {#each matches as match, i}
            <li>
                {match.player1.name}
                <input
                    type="number"
                    min={0}
                    bind:value={match.player1.score}
                    disabled={match.finished} />
                .v.
                <input
                    type="number"
                    min={0}
                    bind:value={match.player2.score}
                    disabled={match.finished} />
                {match.player2.name}
                {#if !match.finished}
                    <button type="button" on:click={finishMatch(match)}>
                        Finish
                    </button>
                {/if}
            </li>
        {/each}
    </ol>
</div> -->

<!-- <div>
    <h1>Table</h1>
    <table>
        <thead>
            <tr>
                <th />
                <th>Player</th>
                <th>GF</th>
                <th>GA</th>
                <th>GD</th>
                <th>PTS</th>
            </tr>
        </thead>
        <tbody>
            {#each [...players].sort((player1, player2) => (player2.pts || 0) - (player1.pts || 0)) as player, i}
                <tr>
                    <td>{i + 1}</td>
                    <td>{player.name}</td>
                    <td>{player.gf || 0}</td>
                    <td>{player.ga || 0}</td>
                    <td>{player.gd || 0}</td>
                    <td>{player.pts || 0}</td>
                </tr>
            {/each}
        </tbody>
    </table>
</div> -->

<!-- <button on:click={reset}>Reset</button> -->

<pre>{JSON.stringify($players, null, 2)}</pre>
