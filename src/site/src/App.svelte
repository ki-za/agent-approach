<script lang="ts">
  import MermaidDiagram from './lib/MermaidDiagram.svelte';

  const pages = [
    { id: 'intent', title: 'Intent' },
    { id: 'workflow', title: 'Bid workflow' },
    { id: 'prototype', title: 'Prototype wedge' },
    { id: 'checks', title: 'Client checks' }
  ];

  let activePage = $state(pages[0].id);

  const currentIndex = $derived(pages.findIndex((page) => page.id === activePage));
  const activeTitle = $derived(pages[currentIndex]?.title ?? 'Workshop');

  const bidWorkflow = `flowchart TD
    A[New bid opportunity] --> B[Create bid intake workspace]
    B --> C[Upload or paste client materials]
    C --> C1[ITT or tender request]
    C --> C2[Project brief]
    C --> C3[Scope of services]
    C --> C4[Programme]
    C --> C5[Contract terms]
    C --> C6[Site information]
    C --> D[Intake Agent extracts structured bid brief]
    D --> E[Go / No-Go Decision Aid]
    E --> E1[Estimate staff time]
    E --> E2[Estimate internal cost]
    E --> E3[Estimate project revenue]
    E --> E4[Estimate win likelihood]
    E --> E5[Check strategic value]
    E --> F{Pursue bid?}
    F -->|No| G[Record no-bid rationale]
    F -->|Yes| H[Criteria Mapper Agent]
    H --> H1[Identify explicit scoring criteria]
    H --> H2[Infer likely hidden criteria]
    H --> H3[Map questions to evidence]
    H --> H4[Suggest case studies / CVs]
    H --> H5[Flag missing information]
    H --> I[Human bid lead reviews plan]
    I --> J{Enough clarity to draft?}
    J -->|No| K[Ask client / directors clarification questions]
    K --> I
    J -->|Yes| L[Draft response structure]
    L --> M[Critical Review Agent]
    M --> M1[Too generic?]
    M --> M2[Evidence missing?]
    M --> M3[Client requirements missed?]
    M --> M4[Overclaiming or unsafe?]
    M --> M5[Weak bespoke fit?]
    M --> N[Human editing and director sign-off]
    N --> O[Bid pack production]
    O --> P[Submit bid]
    P -. future improvement .-> Q[Capture win/loss feedback]
    Q -. future improvement .-> R[Update reusable bid knowledge]`;

  function selectPage(id: string) {
    activePage = id;
  }
</script>

<svelte:head>
  <title>{activeTitle} · Bid Workshop Board</title>
</svelte:head>

<main class="shell">
  <aside class="rail" aria-label="Slide navigation">
    <p class="label">Bid workshop board</p>
    {#each pages as page (page.id)}
      <button
        class:active={activePage === page.id}
        aria-current={activePage === page.id ? 'page' : undefined}
        onclick={() => selectPage(page.id)}
      >
        <span>{page.id}</span>
        {page.title}
      </button>
    {/each}
  </aside>

  <section class="stage" aria-live="polite">
    {#if activePage === 'intent'}
      <article class="hero note">
        <span class="chip evidence label">Evidence-led</span>
        <h1 class="display">Make the bid process inspectable before making it automatic.</h1>
        <p>
          This slide set is a shared workshop surface for checking assumptions with a practice:
          what is true, what is vague, where AI can help, and where humans must remain accountable.
        </p>
      </article>
    {:else if activePage === 'workflow'}
      <article class="flow-page">
        <header>
          <span class="chip decision label">Process map</span>
          <h1 class="headline">Prototype-focused bid workflow</h1>
          <p>Designed to be corrected in conversation, not treated as final truth.</p>
        </header>
        <MermaidDiagram code={bidWorkflow} />
      </article>
    {:else if activePage === 'prototype'}
      <article class="cards-page">
        <header>
          <span class="chip decision label">Chosen wedge</span>
          <h1 class="headline">Criteria Mapper + Critical Review Agent</h1>
        </header>
        <div class="cards">
          <section class="note">
            <p class="label">Criteria mapper</p>
            <h2>Turns the ITT into a bid plan.</h2>
            <p>Extracts questions, predicts likely scoring priorities, and maps each answer to evidence needed.</p>
          </section>
          <section class="note">
            <p class="label">Critical review</p>
            <h2>Finds weak, generic, missing, or unsafe claims.</h2>
            <p>Supports director review without pretending the model owns professional judgment.</p>
          </section>
          <section class="note future-card">
            <p class="label">Future platform work</p>
            <h2>Knowledge library and feedback loop.</h2>
            <p>Previous bids, CVs, case studies, and win/loss feedback can become structured reusable assets later.</p>
          </section>
        </div>
      </article>
    {:else}
      <article class="cards-page">
        <header>
          <span class="chip risk label">Open checks</span>
          <h1 class="headline">Questions for the practice</h1>
        </header>
        <ol class="checklist note">
          <li>What factors decide whether a bid is worth pursuing?</li>
          <li>Where do previous bid answers, CVs, case studies, and images currently live?</li>
          <li>What counts as a strong bid response before director sign-off?</li>
          <li>Which outputs are safe for a first pilot: plan, critique, or draft?</li>
        </ol>
      </article>
    {/if}
  </section>
</main>

<style>
  .shell {
    position: relative;
    z-index: 1;
    display: grid;
    grid-template-columns: 260px minmax(0, 1fr);
    min-height: 100vh;
  }

  .rail {
    position: sticky;
    top: 0;
    height: 100vh;
    padding: 24px;
    border-right: 1px solid var(--rule-line);
    background: color-mix(in srgb, var(--drawing-surface) 92%, white);
  }

  .rail button {
    display: grid;
    gap: 4px;
    width: 100%;
    margin-top: 10px;
    padding: 12px;
    text-align: left;
    color: var(--soft-graphite);
    background: transparent;
    border: 1px solid transparent;
    border-radius: 6px;
    cursor: pointer;
  }

  .rail button span {
    font-family: 'IBM Plex Mono', ui-monospace, monospace;
    font-size: 0.68rem;
    text-transform: uppercase;
  }

  .rail button.active,
  .rail button:hover {
    color: var(--graphite);
    background: var(--paper-panel);
    border-color: var(--rule-line);
  }

  .stage {
    padding: clamp(24px, 5vw, 72px);
  }

  .hero {
    max-width: 980px;
  }

  .hero p,
  header p {
    max-width: 70ch;
    color: var(--soft-graphite);
    font-size: 1.1rem;
    line-height: 1.55;
  }

  .flow-page,
  .cards-page {
    display: grid;
    gap: 24px;
  }

  .cards {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 18px;
  }

  .note h2 {
    margin: 10px 0;
    font-size: 1.25rem;
    line-height: 1.2;
  }

  .note p {
    color: var(--soft-graphite);
    line-height: 1.55;
  }

  .future-card {
    border-color: color-mix(in srgb, var(--future-blue) 55%, var(--rule-line));
  }

  .checklist {
    display: grid;
    gap: 18px;
    max-width: 820px;
    color: var(--soft-graphite);
    font-size: 1.1rem;
    line-height: 1.45;
  }

  @media (max-width: 860px) {
    .shell {
      grid-template-columns: 1fr;
    }

    .rail {
      position: static;
      height: auto;
      border-right: 0;
      border-bottom: 1px solid var(--rule-line);
    }

    .cards {
      grid-template-columns: 1fr;
    }
  }
</style>
