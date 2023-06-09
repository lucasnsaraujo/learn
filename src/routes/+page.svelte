<svelte:head>
    <title>Livros USP</title>
</svelte:head>

<script>
    import data from '../resources/data.json';

    const organizePerPeriod = (data) => data.reduce((acc, subject) => {
        let { period } = subject;
        period = Number(period)

        if (!acc?.[period - 1]?.length) {
            acc[period - 1] = []
        }

        acc[period - 1].push(subject);

        return acc
    }, []).filter(item => item)


    const obligatory = data.filter(item => item.section === 'obligatory');
    const obligatoryPerPeriod = organizePerPeriod(obligatory)

    const elective = data.filter(item => item.section === 'elective');
    const electivePerPeriod = organizePerPeriod(elective)

    const free = data.filter(item => item.section === 'free');
    const freePerPeriod = organizePerPeriod(free);

</script>


<div>
    <h2>Matérias <strong>obrigatórias</strong></h2>
    {#each obligatoryPerPeriod as subjects, index}
        <h3>{subjects[0].period}º período</h3>
        <ul>
            {#each subjects as subject}
            <li>
                <a href={subject.link} target="_blank">{subject.name}</a>
                <ul>
                    <li>{subject.books}</li>
                </ul>
            </li>
            {/each}
        </ul>
    <ul></ul>
    {/each}
</div>

<hr/>

<div>
    <h2>Matérias <strong>eletivas</strong></h2>
    {#each electivePerPeriod as subjects, index}
        <h3>{subjects[0].period}º período</h3>
        <ul>
            {#each subjects as subject}
            <li>
                <a href={subject.link} target="_blank">{subject.name}</a>
                <ul>
                    <li>{subject.books}</li>
                </ul>
            </li>
            {/each}
        </ul>
    <ul></ul>
    {/each}
</div>

<hr/>

<div>
    <h2>Matérias <strong>livres</strong></h2>
    {#each freePerPeriod as subjects, index}
        <h3>{subjects[0].period}º período</h3>
        <ul>
            {#each subjects as subject}
            <li>
                <a href={subject.link} target="_blank">{subject.name}</a>
                <ul>
                    <li>{subject.books}</li>
                </ul>
            </li>
            {/each}
        </ul>
    <ul></ul>
    {/each}
</div>


