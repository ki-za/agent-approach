<script lang="ts">
  import mermaid from 'mermaid';

  let { code }: { code: string } = $props();
  let rendered = $state('');

  mermaid.initialize({
    startOnLoad: false,
    theme: 'base',
    themeVariables: {
      background: '#FBF7EE',
      primaryColor: '#FBF7EE',
      primaryTextColor: '#25221D',
      primaryBorderColor: '#CFC5B5',
      lineColor: '#5B554B',
      secondaryColor: '#F3EFE7',
      tertiaryColor: '#E5DCCF',
      fontFamily: 'Inter, Arial, sans-serif'
    },
    flowchart: {
      curve: 'basis',
      padding: 12
    }
  });

  $effect(() => {
    const id = `mermaid-${Math.random().toString(36).slice(2)}`;
    mermaid.render(id, code).then(({ svg }) => {
      rendered = svg;
    });
  });
</script>

<div class="diagram-shell">
  <!-- Static Mermaid output generated from local diagram strings. -->
  {@html rendered}
</div>

<style>
  .diagram-shell {
    overflow: auto;
    max-height: 72vh;
    padding: 18px;
    background: var(--paper-panel);
    border: 1px solid var(--rule-line);
    border-radius: 12px;
  }

  .diagram-shell :global(svg) {
    width: 100%;
    min-width: 920px;
    height: auto;
  }
</style>
