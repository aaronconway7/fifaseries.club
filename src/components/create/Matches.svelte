<script>
    import { players } from '../../store.js'

    let matches = []

    const addMatch = () => {
        matches = [
            ...matches,
            { player1: { ...$players[0] }, player2: { ...$players[1] } },
        ]
    }
</script>

<button type="button" on:click={addMatch}>Add Match</button>

{#each matches as match, i}
    <div>
        <select bind:value={match.player1}>
            {#each $players as player, i}
                <option value={player}>{player.name}</option>
            {/each}
        </select>
        <input
            type="number"
            min={0}
            bind:value={match.player1.score}
            disabled={match.finished} />
        <span>v</span>
        <select bind:value={match.player2}>
            {#each $players as player, i}
                <option value={player}>{player.name}</option>
            {/each}
        </select>
        <input
            type="number"
            min={0}
            bind:value={match.player2.score}
            disabled={match.finished} />
        <button type="button">Finish</button>
    </div>
{/each}

<pre>{JSON.stringify(matches, null, 2)}</pre>
