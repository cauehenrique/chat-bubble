<script lang="ts">
  export let text: string
</script>

<div id="message">
  <span>{text}</span>
</div>

<style>
  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(5px);
    }
    to {
      opacity: 1;
      transform: translateY(0px);
    }
  }

  @keyframes fadeOut {
    from {
      opacity: 1;
      transform: translateY(0px);
    }
    to {
      opacity: 0;
      transform: translateY(-5px);
    }
  }

  #message {
    width: fit-content;
    max-width: 500px;

    font-size: 2rem;
    background-color: #fff;
    padding: 0.75rem 0.95rem;
    border-radius: 0.95rem;

    animation: fadeIn, fadeOut;
    animation-duration: 0.25s;
    animation-delay: 0s, 15s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-out;
  }
</style>
