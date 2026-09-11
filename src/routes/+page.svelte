<script>
  import EmailIcon from "$lib/components/icons/EmailIcon.svelte";
  import GithubIcon from "$lib/components/icons/GithubIcon.svelte";
  import LinkedinIcon from "$lib/components/icons/LinkedinIcon.svelte";
  import PhoneIcon from "$lib/components/icons/PhoneIcon.svelte";
  import WebsiteIcon from "$lib/components/icons/WebsiteIcon.svelte";
  import ThemeSwitch from "$lib/components/ThemeSwitch.svelte";

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
    <ThemeSwitch />
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
  main {
    display: grid;
    height: 100dvh;
    place-items: center;
  }

  article {
    background-color: var(--bg);
    position: relative;
    display: grid;
    grid-template-rows: max-content max-content max-content 1fr;
    height: 100dvh;
    justify-items: center;
    grid-template-areas:
      "figure"
      "name"
      "job"
      "links";

    @media (min-width: 800px) {
      height: clamp(400px, 33.33vw, 600px);
      aspect-ratio: 1.6 / 1;
      grid-template-columns: 1fr 1fr;
      grid-template-rows: max-content max-content 1fr;
      grid-template-areas:
        "figure name"
        "figure job"
        "figure links";
      justify-items: start;
    }
  }

  figure {
    background: linear-gradient(
      var(--primary),
      var(--primary) 50%,
      var(--bg) 50%
    );
    display: grid;
    grid-area: figure;
    padding: 2rem 0;
    place-items: center;

    @media (min-width: 800px) {
      background: linear-gradient(
        to right,
        var(--primary),
        var(--primary) 50%,
        var(--bg) 50%
      );
    }

    img {
      aspect-ratio: 1;
      border-radius: 50%;
      object-fit: cover;
      width: clamp(225px, 75%, 250px);
    }
  }

  h1 {
    color: var(--content);
    grid-area: name;

    @media (min-width: 800px) {
      padding-top: clamp(2rem, 5.33vw, 4rem);
    }
  }

  h2 {
    grid-area: job;
    font-weight: normal;
  }

  ul {
    align-content: center;
    display: grid;
    grid-template-rows: repeat(5, max-content);
    gap: 1.5rem;
    grid-area: links;

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
