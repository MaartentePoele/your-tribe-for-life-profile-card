<label>
  <input type="checkbox" id="theme-switch" />
  <svg class="sun-icon">
    <circle cx="12" cy="12" r="4"></circle>
    <path d="M12 2v2"></path>
    <path d="M12 20v2"></path>
    <path d="m4.93 4.93 1.41 1.41"></path>
    <path d="m17.66 17.66 1.41 1.41"></path>
    <path d="M2 12h2"></path>
    <path d="M20 12h2"></path>
    <path d="m6.34 17.66-1.41 1.41"></path>
    <path d="m19.07 4.93-1.41 1.41"></path>
  </svg>
  <svg class="moon-icon">
    <path d="M12 3a6 6 0 0 0 9 9 9 9 0 1 1-9-9Z"></path>
  </svg>
</label>

<style>
  label {
    cursor: pointer;
    position: absolute;
    top: 1.5rem;
    right: 1.5rem;
    background-color: var(--bg);
    padding: 0.25rem;
    border-radius: 50%;

    input {
      display: none;
    }

    .sun-icon,
    .moon-icon {
      transition: all 0.15s ease-in-out;

      width: 1.5rem;
      height: 1.5rem;

      fill: none;
      stroke: currentColor;
      stroke-width: 2;
      stroke-linecap: round;
      stroke-linejoin: round;
    }

    .sun-icon:hover,
    .moon-icon:hover {
      stroke: var(--primary);
    }
  }
</style>
