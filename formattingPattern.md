
# Table of Contents

-   [Problem](#orgf611eb7)
-   [Current examples](#orgf2814be)
-   [Suggested solution](#orgdb99502)
-   [Considerations](#orgf3dd310)

 <br>


<a id="orgf611eb7"></a>

# Problem

-   Community has expressed need to send ****styled textual information**** via GDSN.

-   `FormattedDescription` and `formattingPattern` provide this

-   But these are difficult to implement and use

-   HTML code is currently used by some datapools, but:
    -   Unstandardized
    -   Unsafe
    -   Must be escaped/unescaped
    -   Not adapted to current XML modeling

 <br>

---

 <br>


<a id="orgf2814be"></a>

# Current examples

-   TIIG framework

        formattingPattern=“(1,p),(1,em),(56,/em),(141,em),(159,/em),(214,em),(266,/em),(348,em),(362,/em),
                           (446,em),(456,/em),(457,/p),(459,p),(459,em),(512,/em),(556,em),(578,/em),(604,em),(622,/em),
                           (775,em),(784,/em),(806,em),(838,/em),(850,em),(886,/em),(906,em),(926,/em),(957,em),(967,/em),(969,/p)">

-   HTML

        <stringAVP attributeName="ingredientStatementFormattingPattern">&lt;u&gt;Stuff&lt;/u&gt;</stringAVP>
        <stringAVP attributeName="ingredientStatementFormattingPattern">stuff&lt;br&gt;Ingredients: Stuff</stringAVP>
    
     <br>
    
    ---
    
     <br>


<a id="orgdb99502"></a>

# Suggested solution

-   Implement [BBCode formatting](https://www.bbcode.org/how-to-use-bbcode-a-complete-guide.php) or similar [lightweight markup language](https://en.wikipedia.org/wiki/Lightweight_markup_language).

    -   Simple
    
    -   Safe
    
    -   Flexible
    
    -   Well-established
    
    -   Syntax
    
        <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
        
        
        <colgroup>
        <col  class="org-left" />
        
        <col  class="org-left" />
        </colgroup>
        <thead>
        <tr>
        <th scope="col" class="org-left">BBCode</th>
        <th scope="col" class="org-left">Effect</th>
        </tr>
        </thead>
        
        <tbody>
        <tr>
        <td class="org-left">[b]</td>
        <td class="org-left">Bold</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[i]</td>
        <td class="org-left">Italic</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[u]</td>
        <td class="org-left">Underline</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[br]</td>
        <td class="org-left">Line break</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[url]</td>
        <td class="org-left">Insert link</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[color=color]</td>
        <td class="org-left">Change text color to {color}</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[align=alignment]</td>
        <td class="org-left">Align text e.g. to center</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[list]</td>
        <td class="org-left">Make list</td>
        </tr>
        
        
        <tr>
        <td class="org-left">[*]</td>
        <td class="org-left">Add list item</td>
        </tr>
        </tbody>
        </table>
    
    -   Example BBCode
    
            [b]4 X Flamin’ Hot Flavour Baked Corn Snack. Ingredients: [/b]Maize, Vegetable Oil, Flamin Hot Flavour [b]Hydrolysed Soya Protein[/b], [i]Fructose[/i], Flavourings ...
        
         <br>

-   Suggested process:

    -   Service providers implement rich-text editors in their GUIs, or &#x2026;
    
    -   End users fill in TII, by hand.
    
    -   DP forwards TII to recipient
    
    -   Recipient decides how or whether to handle styled TII.
    
         <br>


<a id="orgf3dd310"></a>

# Considerations

-   Limit complexity: Agree on allowed subset of BBCode?

-   Modeling: Replace `formattingPattern`, `sequenceNumber`?

-   Validations: For all styled text, ensure recipients get same text unstyled?

     <br>

