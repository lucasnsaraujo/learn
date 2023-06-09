<script>
	import data from '../resources/data.json';
	import Card from '../components/List/Card.svelte';
	import '../styles.css';

	const obligatory = data.filter((item) => item.section === 'obligatory');

	const elective = data.filter((item) => item.section === 'elective');

	const free = data.filter((item) => item.section === 'free');
</script>

<svelte:head>
	<title>Livros USP</title>
</svelte:head>

<main>
	<header>
		<h1>Ciência da Computação para Autodidatas</h1>
		<p>
			Bem-vindo ao nosso site! Aqui você encontrará recursos de aprendizado de alta qualidade
             para estudantes e desenvolvedores autodidatas interessados em Ciência da Computação. 
             Organizamos o material do curso da Universidade de São Paulo por período, com matérias 
             obrigatórias, eletivas e livres, juntamente com uma seleção de livros recomendados. 
             Explore nosso conteúdo e aproveite para expandir seu conhecimento na área. Bons estudos!
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
