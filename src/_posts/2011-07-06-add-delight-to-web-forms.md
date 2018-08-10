---
title: 'Add delight to web forms (with code sample)'
date: '2011-07-06 09:54'
tags:
    - Ajax
    - city
    - form
    - HTML
    - Javascript
    - jQuery
    - JSON
    - 'postal code'
    - 'User Experience'
category: 'User Experience'
slug: add-delight-to-web-forms-with-code-sample
---

Marking up and styling forms in HTML and CSS is something you either love or hate. Personally I love it, since it's one of these things I can be really nitty-picky with – to iterate and iterate over the appearance and behavior of the form. "Is this simple enough? Is this section necessary? Should we separate this from that?", and so on.

## Exhibit A: "How many copy may I get you?"
[ ![Panic Transmit](http://johanbrook.com/core/wp-content/uploads/2011/07/Panic-Transmit-1-copy.png) ](http://johanbrook.com/core/wp-content/uploads/2011/07/Panic-Transmit-1-copy.png) Everything looks as it should do. Nothing unusual. [ ![Panic Transmit](http://johanbrook.com/core/wp-content/uploads/2011/07/Panic-Transmit-3-copies.png) ](http://johanbrook.com/core/wp-content/uploads/2011/07/Panic-Transmit-3-copies.png) Try changing the amount of copies, and watch the grammar of the sentence change as well. Also: switch between the "Transmit 4" and "Transmit 4 Upgrade" options and see the sentences change.
## Exhibit B: "Are we there yet?"
In the same form, scroll to the bottom and you'll find the submit button disguised as a progress meter. It'll update live as you complete the form, giving you instant feedback on the eternal question: "Did I get 'em all now?".
## A quick example of nice UX:
How to you add delight to a form, without writing a whole jQuery plugin for it? Let's say you have a sign up form which includes a postal code and city.

    <form method="POST" action="">
    	<label>Postal code 
    		<input type="text" placeholder="810 20" id="postal-code" />
    	</label>
    	
    	<label>City 
    		<input type="text" placeholder="City" id="city" />
    	</label>
    </form>
That code would produce this:

    $("#postal-code").blur(function(){ 
    	var url = "http://postnummersok.se/api?callback=?",
    		// remove whitespace in postal code 
    		code = encodeURI(this.value.replace(/s+/g, "")); 
    		
    	$.getJSON(url, {q: code}, function(json){ 
    		if(json === null) return; 
    		
    		$("#city").val(json[0]).select(); 
    	}); 
    });
As you can see I'm using jQuery in this example. A simple `blur` event is binded to the postal code field, and the API URL is defined. Note the `?callback=?` piece, which tells the jQuery XHR to treat the call as JSONP [(read more in the API)](http://api.jquery.com/jQuery.getJSON/#jsonp).
## Outro
When building forms: put some effort into it, and use your fantasy. "How could I make this super boring form really awesome, easy, and even fun to fill in?". Add delight, but don't get in the visitor's way. Add helpful validation messages, and other help text without bloating the whitespace. Form building is truly a form of art, therefore: iterate, iterate, iterate.