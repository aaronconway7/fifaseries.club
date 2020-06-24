<script>
    import { v4 as uuidv4 } from 'uuid'

    import { players } from '../../store.js'

    const addPlayer = () => {
        players.update(p => [...p, { id: uuidv4(), name: '', squad: [] }])
    }

    const addSquadMember = player => {
        players.update(p => {
            const playerToUpdate = p.find(pl => pl.id === player.id)
            playerToUpdate.squad = [
                ...playerToUpdate.squad,
                { id: uuidv4(), name: '', goals: 0 },
            ]

            return p
        })
    }
</script>

<div>
    {#each $players as player, i}
        <input
            placeholder={`Player ${i + 1}`}
            bind:value={player.name}
            required />
        <div>
            <h2>Squad</h2>
            {#each player.squad as squadMember, i}
                <input
                    placeholder={`Member ${i + 1}`}
                    bind:value={squadMember.name}
                    required />
            {/each}
            <button type="button" on:click={addSquadMember(player)}>
                Add Squad Member
            </button>
        </div>
    {/each}
    <button type="button" on:click={addPlayer}>Add Player</button>
</div>
