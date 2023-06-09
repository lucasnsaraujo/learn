<script>
	export let title;
	export let subjectsArray;

	const organizePerPeriod = (data) =>
		data
			.reduce((acc, subject) => {
				let { period } = subject;
				period = Number(period);

				if (!acc?.[period - 1]?.length) {
					acc[period - 1] = [];
				}

				acc[period - 1].push(subject);

				return acc;
			}, [])
			.filter((item) => item);
</script>

<h2>{title}</h2>
<div class="card">
	{#each organizePerPeriod(subjectsArray) as subjects, index}
		<div class="period">
			<h4>{subjects[0].period}º período</h4>
			{#each subjects as subject}
				<div class="content">
					<h5>
						<a href={subject.link} target="_blank">{subject.name}</a>
					</h5>
					<ul>
						<li>{subject.books}</li>
					</ul>
				</div>
			{/each}
		</div>
	{/each}
</div>

<style>
	h2 {
		color: #ebf1f4;
        margin-bottom: 20px;
        text-align: center;
        border-radius: 6px;
        padding: 20px;
        background-color: #3c2a4d;
	}

	h4 {
		text-transform: uppercase;
        margin-bottom: 15px;
        background-color: #3c2a4d;
        border-radius: 6px;
        padding: 10px;
        max-width: max-content;
        font-weight: bold;
        color: #ebf1f4;
	}
	h5 {
		text-transform: uppercase;
        color: #3c2a4d;
        font-size: 1.4rem;
        margin-bottom: 10px;
	}

    h5 > a {
        text-decoration: none;
        color: unset;
    }

    h5 > a:visited {
        color: unset;
    }

    h5:hover {
        filter: opacity(0.5);
        transition: all 0.15s ease-in-out;
        text-decoration: underline;
    }

	li {
		line-break: anywhere;
        margin-left: 15px;
        list-style: none;
        color: #503a65;
	}

	.card {
		border-radius: 6px;
		/* background-color: #95adbe; */
		margin-bottom: 80px;
	}
    .content {
        margin-bottom: 30px;
    }
</style>
