<script>
    import CopyButton from "./CopyButton.svelte";
    import CopiedButton from "./CopiedButton.svelte";
  
    let showTooltip = false;
    let CurrentIcon = CopyButton; // Default icon component
  
    console.log("rerendered");
    
    function copyToClipboard() {
     
    
     CurrentIcon = CopiedButton; // Switch to CopiedButton
  
      
      setTimeout(() => {  
        CurrentIcon = CopyButton; // Switch back to CopyButton
      }, 2000);
    }
  </script>
  
  <button
    on:click={copyToClipboard}
    class="copy-button"
  >
    <svelte:component this={CurrentIcon} />
  </button>
  
  <style>
    .copy-button {
      position: relative;
      background: none;
      border: none;
      cursor: pointer;
      padding: 0;
    }
     
  </style>
  