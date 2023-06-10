<script>
	import data from '../resources/data.json';
	import Card from '../components/List/Card.svelte';
	import '../styles.css';

	const obligatory = data.filter((item) => item.section === 'obligatory');

	const elective = data.filter((item) => item.section === 'elective');

	const free = data.filter((item) => item.section === 'free');
</script>

<svelte:head>
	<title>Autodidatas - Ciência da Computação</title>
</svelte:head>

<main>
	<header>
		<h1>Ciência da Computação para Autodidatas</h1>
		<p>
			Bem-vindo ao nosso site! Catalogamos aqui os livros necessários em uma graduação no curso de
			Ciência da Computação, para que desenvolvedores ou estudantes autodidatas possam expandir seus
			conhecimentos. Bons estudos! (Inspirado por: teachyourselfcs.com)
		</p>
	</header>

	<Card title="Matérias obrigatórias" subjectsArray={obligatory} />
	<Card title="Matérias eletivas" subjectsArray={elective} />
	<Card title="Matérias livres" subjectsArray={free} />
</main>

<style>
	main {
		max-width: 1125px;
		margin: 0 auto;
		padding: 20px;
	}

	header {
	}
	header > h1 {
		text-align: center;
        color: #574f7d;
        padding-bottom: 10px;
        font-weight: 900;
	}
    header > p {
        text-align: left;
        color: #574f7d;
        padding-bottom: 40px;
    }



</style>
