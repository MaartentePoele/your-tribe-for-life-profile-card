<script>
  import EmailIcon from "$lib/components/icons/EmailIcon.svelte";
  import GithubIcon from "$lib/components/icons/GithubIcon.svelte";
  import LinkedinIcon from "$lib/components/icons/LinkedinIcon.svelte";
  import PhoneIcon from "$lib/components/icons/PhoneIcon.svelte";
  import WebsiteIcon from "$lib/components/icons/WebsiteIcon.svelte";

  let { data } = $props();
  const person = data.person;

  function formatEmail(name) {
    return name.replaceAll(" ", ".").toLowerCase();
  }

  function formatLinkedIn(name) {
    return name.replaceAll(" ", "-").toLowerCase();
  }
</script>

<main>
  <article>
    <figure>
      <img
        src="https://fdnd.directus.app/assets/{person.mugshot_year2}"
        alt="Profielfoto van {person.name}"
      />
    </figure>

    <h1>{person.name}</h1>
    <h2>Frontend Developer</h2>
    <ul>
      <li>
        <PhoneIcon />
        06-12345678
      </li>
      <li><EmailIcon />{formatEmail(person.name)}@hva.nl</li>
      <li>
        <a href={person.website} target="_blank">
          <WebsiteIcon />
          Portfolio</a
        >
      </li>
      <li>
        <a
          href="https://www.linkedin.com/in/{formatLinkedIn(
            person.name,
          )}-3a7a57332/"
          target="_blank"
        >
          <LinkedinIcon />
          LinkedIn</a
        >
      </li>
      <li>
        <a href="https://github.com/{person.github_handle}" target="_blank">
          <GithubIcon />
          GitHub</a
        >
      </li>
    </ul>
  </article>
</main>

<style>
  article {
    background-color: var(--bg);
    display: grid;
    grid-template-rows: max-content max-content max-content 1fr;
    height: 100dvh;
    justify-items: center;
  }

  figure {
    background: linear-gradient(
      var(--primary),
      var(--primary) 50%,
      var(--bg) 50%
    );
    display: grid;
    padding: 2rem 0;
    place-items: center;

    img {
      aspect-ratio: 1;
      border-radius: 50%;
      object-fit: cover;
      width: clamp(225px, 75%, 250px);
    }
  }

  h1 {
    color: var(--content);
  }

  ul {
    align-content: center;
    display: grid;
    grid-template-rows: repeat(5, max-content);
    gap: 1.5rem;

    li {
      align-items: center;
      color: var(--content);
      display: flex;
      gap: 0.5rem;

      a {
        display: flex;
        color: var(--content);
        gap: 0.5rem;

        &:hover {
          color: var(--primary);
        }
      }
    }
  }
</style>
