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

		const booksOrganizedPerPeriod = organizePerPeriod(subjectsArray)

		const shouldRenderPeriodTitle = (books) => books.reduce((acc, value) => value.books.length ? acc + 1 : 0 , 0)

		const generateAmazonRedirect = (title) => `https://www.google.com/search?q=${encodeURIComponent(title)}`
</script>

<h2>{title}</h2>
<div class="card">
	{#each booksOrganizedPerPeriod as subjects, index}
		<div class="period">
			{#if !!shouldRenderPeriodTitle(subjects)}
			<h4>{subjects[0].period}º período</h4>
			{#each subjects as subject}
				{#if subject.books.length}
				<div class="content">
					<h5>
						{subject.name}
					</h5>
					<ul>
						{#each subject.books as book}
							<li><a href={generateAmazonRedirect(book)} target="_blank">{book}</a></li>
						{/each}
					</ul>
				</div>
				{/if}
			{/each}
			{/if}
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
		user-select: none;
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
		user-select: none;
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


	li {
        margin-left: 15px;
        list-style-type: circle;
        color: #503a65;
		cursor: pointer;
	}

	li > a:visited {
		text-decoration: none;
		color: unset;
	}
	li > a {
		text-decoration: none;
		color: unset;
	}

	li:hover {
		filter: invert(0.5);
		margin-left: 20px;
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
