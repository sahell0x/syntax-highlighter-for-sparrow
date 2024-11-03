<script>
  import Copy from './Copy.svelte';
  import Prism from 'prismjs';
  import 'prismjs/themes/prism-tomorrow.min.css'; // Your preferred theme
  import 'prismjs/components/prism-javascript'; // Import specific language
  import 'prismjs/components/prism-java';
  import Copy2 from './Copy2.svelte';
  import CopyButton from './CopyButton.svelte';
  import Button from './Button.svelte';
  
  let code = `
import java.util.Scanner;

public class HelloWorld {

    public static void main(String[] args) {

        // Creates a reader instance which takes
        // input from standard input - keyboard
        Scanner reader = new Scanner(System.in);
        System.out.print("Enter a number: ");

        // nextInt() reads the next integer from the keyboard
        int number = reader.nextInt();

        // println() prints the following line to the output screen
        System.out.println("You entered: " + number);
    }
}`;

  let language = 'java';

  $: {
    setTimeout(() => {
      Prism.highlightAll();
    }, 0);
  }

  function copyToClipboard() {
    navigator.clipboard.writeText(code).then(() => {
    }).catch(err => {
    });
  }
</script>

<div class="code-box">
 <button class="copy-button" on:click={copyToClipboard}> <Button></Button></button>

  <pre class="code-container line-numbers">
    <code class={`language-${language}`}>{code}</code>
  </pre>
</div>

<style>
  .code-box {
    position: relative; /* Create a relative positioning context */
    display: inline-block; /* Ensure the button stays inside the box */
  }

  

  .copy-button {
    position: absolute;
    top: 10px; /* Adjust as needed */
    right: 10px; /* Adjust as needed */
    padding: 5px 10px;
    border: none;
    border-radius: 3px;
    cursor: pointer;
    background: none;
  }

  .code-container {
    width: 600px; /* Set the width of the code block */
    max-height: 300px; /* Set the maximum height */
    overflow-x: auto; /* Horizontal scroll */
    overflow-y: auto; /* Vertical scroll if needed */
    border: 1px solid #444; /* Darker border for better contrast */
    border-radius: 5px;
    background-color: #2d2d2d; /* Dark background for code block */
    padding: 16px; /* Optional padding for content */
}

/* Custom scrollbar styles for WebKit browsers */
.code-container::-webkit-scrollbar {
    width: 8px; /* Width of the vertical scrollbar */
    height: 8px; /* Height of the horizontal scrollbar */
}

.code-container::-webkit-scrollbar-track {
    background: #22232e; /* Background of the scrollbar track */
    border-radius: 10px; /* Rounded corners for track */
}

.code-container::-webkit-scrollbar-thumb {
    background: #555; /* Color of the scrollbar thumb */
    border-radius: 10px; /* Rounded corners for thumb */
}

.code-container::-webkit-scrollbar-thumb:hover {
    background: #777; /* Change color on hover for better visibility */
}

/* For Firefox */
.code-container {
    scrollbar-width: thin; /* Set scrollbar width to thin */
    scrollbar-color: #555 #22232e; /* Set thumb color and track color */
}

</style>
