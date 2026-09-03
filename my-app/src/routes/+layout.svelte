<script>
  import favicon from "$lib/assets/favicon.svg";

  let { children, data } = $props();

  const persons = data.persons;
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

<aside>
  {#each persons as person}
    <a href="/person/{person.id}">
      <img
        src="https://fdnd.directus.app/assets/{person.mugshot}"
        alt=""
        width="100"
      />
    </a>
  {/each}
</aside>

<main>
  {@render children()}
</main>
