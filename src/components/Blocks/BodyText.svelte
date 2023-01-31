<script>
     import { marked } from 'marked';
     export let text;
     export let align;
     
     if(align == 'Left') {
        align = 'text-left';
     }
        else if(align == 'Right') {
            align = 'text-right';
        }
        else if(align == 'Center') {
            align = 'text-center';
        }
        else {
            align = 'text-left';
        }

    if (!text)
        throw new Error(
        '"text" prop must be defined as a string'
        );

    // Go through all text, replace \n with <br>
    // if it is \r\n\r\n\r\n, replace with a <br><br> and newline
    text = text.replace(/\r\n\r\n\r\n/g, "<br><br>");
    text = text.replace(/\n/g, "<br>");
    // If there are numbers like [3], replace them with <sup>3</sup>
    text = text.replace(/\[(\d+)\]/g, "<sup>$1</sup>");
    // If there are any numbers at the end of a sentence, make them <sup>3</sup>
    text = text.replace(/^\d+/g, "<sup><a href=\"#endnote$1\">$1</a></sup>");


</script>

<section class="body-text {align}">
    {@html marked(text)}
  </section>
