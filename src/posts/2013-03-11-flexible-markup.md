---
title: 'Tags and class names – on building flexible markup'
date: '2013-03-11 08:14'
tags:
  - CSS
  - HTML
  - Markup
  - semantic
  - classes
  - 'class names'
category: HTML
---

**It is said your markup** should be _clean_ and _semantic_. What does that mean, exactly? As few tags as possible? The correct tags for the job? Few or no ID and class attributes? At least that's been the main formula for a while now. Littering ID and class attributes over your markup has been frowned upon. But what does the alternative mean?

    <footer>
    	<h2>Joe Doe</h2>
    
    	<img src="avatar-joe.jpg" alt="Joe" />
    
    	<p>
    One morning, when Gregor Samsa woke from troubled dreams, he found himself transformed in his bed into a horrible vermin. He lay on his armour-like back, and if he lifted his head a little he could see his brown belly, slightly domed and divided by arches into stiff sections.
    	</p>
    	
    </footer>
Minimal but good example of clean HTML. But a bit naïve. How would you style the image avatar in CSS? Piece of cake (assuming the `footer` element is in an `article` ):

    article footer img {
    	float: left;
    }
Okay. But say you wrap the `img` tag in a `figure` for example? Then your styling perhaps doesn't behave as expected. If you add more images in the box, weird stuff may happen as well.

    <footer class="post-author">
    	<h2>Joe Doe</h2>
    
    	<figure class="author-avatar">	
    		<img src="avatar-joe.jpg" alt="Joe" />
    	</figure>
    
    	<div class="author-bio">
    		<p>
    			One morning, when Gregor Samsa woke from troubled dreams, he found himself transformed in his bed into a horrible vermin. He lay on his armour-like back, and if he lifted his head a little he could see his brown belly, slightly domed and divided by arches into stiff sections.
    		</p>
    	</div>
    </footer>
Above you see the markup I would write. Notice the additional `class` attributes and the `div` element wrapper.
## But why, oh why?
Because it lets me write **more robust, flexible and portable HTML**. In my CSS, I don't rely on element tags (which may change during time). As long as I don't nest the styling too far, my markup will stay the same if I decide to alter the HTML structure (which as you know always happens). 