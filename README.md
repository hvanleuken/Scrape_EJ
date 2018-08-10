# Scrape_EJ
html/javascript exercise to scrape the news of edmontonjournal.com

Scrape_EJ.html:

Read 'webPage' and show the news items based on 'selector' in the a selection
list. Articles containing 'ignore' words do not make it into the list.
For each list-item, when selected, show the article.

The source webPage and Articles are not parsed by the browser so loading ads
and running source JavaScript is prevented.

/Todo:
1) Give odd and even list items a different colour to improve readability?
2) Empty 'entry-content' div's in the news items could be removed but do not interfere.
3) Include comment section.
4) Give focus to the article selected from the list. Now, after the first article
   "news-item" gets focus at the bottom of the page and has to be clicked to get
   to the article. The next selected article does get focus as it was intended.
5) Explore http://edmontonjournal.com/news-sitemap.xml as source for first input to
   Scrape_EJ. $1 from <loc>(.{0,300})</loc> will get the article urls.

</article>

/Questions and remarks:
1) jQuery(article).remove("nav") does not work.
2) The following setting focus attempts do not work:
  a) $.when( $.ready ).then($(".display").focus());
  b) $.when( $(".display").ready ).then($(".display").focus());
  c) document.getElementById("news-item").focus();
  d) <a id="linkID" href="#news-item">bla</a> // Does not get focus without href="#news-item"
Focus() is an issue when reading on the internet. Only works for certain elements and
even then ... Documentation is crap.

  Safari 10.1.2, MacOS Sierra 10.12.6
  jQuery JavaScript Library v3.2.1

3) These next lines give a favicon in the bookmarks list.
<link rel="profile" href="http://gmpg.org/xfn/11">
<link rel="icon"          type="image/png" href="http://1.gravatar.com/blavatar/9db188f8de0c78297ec188789805e471?s=32" sizes="16x16">
<link rel="shortcut icon" type="image/x-icon" href="http://1.gravatar.com/blavatar/9db188f8de0c78297ec188789805e471?s=32" sizes="16x16">

They are gone from the bookmarks after clearing of history, do show up in the url textbox
when selecting the file but not when selecting the bookmark.
Both type="image/png" or type="image/x-icon" work and only the rel="icon" link seems to
do the job already.



  --------------------
  Todo 3)
  // Comments are in : <div id="comments" class="comments-area">
  //$.get(value, "",
  //      function(data) {
  //        var article = jQuery(data).find(pageParts[1]);  // debug: document.myHTML = article;
  //        document.myHTML = article;
          // Only part of pageParts[1] is loaded. fb_iframe_widget related stuff is missing.
          // 'find' pageParts[] in one go?

          //for (var i = 0; i < remove.length; i++) {
          //  article.find(remove[i]).remove();      // Remove some stuff before presenting.
          //}

  //        $( ".display" ).append(article);
  //      },
  //      "html"
  //); // get()
