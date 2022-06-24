<script lang="ts">
  import { getName } from "@tauri-apps/api/app";
  import { sendNotification } from "@tauri-apps/api/notification";

  export let name: string;
  (async () => {
    name = await getName();
  })();

  function browserNotification() {
    new Notification(`We're called ${name}`, {
      body: "See that icon?",
    });
  }

  function tauriNotification() {
    sendNotification({
      title: "Hello Flatpak",
      body: "Tauri is awesome!",
    });
  }
</script>

<main>
  <h1>{name}!</h1>
  <p>
    <img src="favicon.png" width="16" alt="little icon" />
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>
  <p>
    <button class="button" on:click={browserNotification}
      >Browser notification</button
    >
    <button class="button" on:click={tauriNotification}
      >Browser notification</button
    >
  </p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
