<script>
  let { data } = $props();

  const persons = data.persons;
</script>

<h1>Home</h1>
{#each persons as person}
  <a href="/{person.id}">
    <img src="https://fdnd.directus.app/assets/{person.mugshot}" alt="" width="100"/>
  </a>
{/each}
