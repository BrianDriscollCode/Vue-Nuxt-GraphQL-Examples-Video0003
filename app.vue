<template>
    <p v-for="(item, name) in data.characters.results"> Name: {{ item.name }} | Gender: {{ item.gender }} </p>
</template>

<script setup>
  const getCharacters = gql`
	query {
		characters {
			results {
				name,
				gender
			}
		}
	}
  `
  const variables = { limit: 40 }
  const { data } = await useAsyncQuery(getCharacters, variables)
  console.log(data.value);

  </script>