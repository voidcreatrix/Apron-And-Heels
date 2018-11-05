
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <!-- Game Title: edit this -->
    <title>Undum</title>
    <!-- End of Game Title -->

    <!-- Remove this if you don't use the Tangerine font in your
         stylesheet -->
    <link href='http://fonts.googleapis.com/css?family=Tangerine'
          rel='stylesheet' type='text/css'>

    <!-- This is your game's stylesheet, modify it if you like. -->
    <link media="screen"
          rel="stylesheet" href="media/css/undum.css">

    <!-- Suppport for mobile devices. -->
    <meta name="viewport" content="user-scalable=no, width=device-width">
    <link rel="apple-touch-icon" href="media/img/iphone/icon.png">
    <link rel="apple-touch-startup-image" href="media/img/iphone/splash.png">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <!--[if !IE]>-->
    <link media="only screen and (max-width: 640px)"
          rel="stylesheet" type="text/css" href="media/css/undum-mobile.css">
    <!--<![endif]-->

  </head>
  <body>
    <!-- This isn't needed and isn't visible in desktop versions,
         because we can display the character information and the
         tools onscreen all the time. -->
    <div id="toolbar">
      <!-- Set this to be a small version of the title, for the
           toolbar on mobile devices. -->
      <h1>Undum</h1>
      <div class="nav">
        <a href="#" class="button" id="menu-button">Menu</a>
      </div>
    </div>
    <ul id="menu">
      <li><a href="#title, #content_wrapper">Story</a></li>
      <li><a href="#character_panel">Character</a></li>
      <li><a href="#info_panel">Info</a></li>
    </ul>

    <div id="page">

      <div id="tools_wrapper">
        <div id="info_panel" class="tools left">

          <!-- Game Background: edit this -->
          <h1>Undum</h1>
          <p>
            Undum is a pure client-side game framework for narrative
            interactive fiction. It is designed for HTML&#x200A;5 and
            CSS&#x200A;3. You can read more and download the source
            code <a href="http://github.com/idmillington/undum">here</a>.
          </p>
          <!-- End of Game Background -->

          <div class='buttons'>
            <button id="save">Save</button><button id="erase">Erase</button>
          </div>
        </div>

        <div id="character_panel" class="tools right">
          <h1>Character</h1>
          <div id="character">
            <div id="character_text">
              <div id="character_text_content"></div>
            </div>
            <div id="qualities"></div>
          </div>
        </div>
      </div> <!-- End of div.tools_wrapper -->

      <div id="mid_panel">
        <div id="title">
          <div class="label">

            <!-- Game Title: edit this -->
            <h1>The Undum Tutorial <span class='fancy'>&amp;</span><br>
              Interactive Example</h1>
            <h2>by I D Millington</h2>
            <!-- End of Game Title -->

            <noscript><p class="noscript_message">This game requires 
              Javascript.</p></noscript>
            <p class="click_message">click to begin</p>
          </div>
        </div>

        <div id="content_wrapper">
          <div id="content">
          </div>
          <a name="end_of_content"></a>
        </div>

        <div id="legal">
          <!-- Your Copyright: edit this -->
          <p>Content and additional software and design &copy; 2010 IDM.</p>
          <!-- End of Your Copyright -->

          <!-- This line is totally optional. -->
          <p>Created with <a href="http://idmillington.github.io/undum/">Undum</a>.</p>
        </div>
      </div>
    </div> <!-- End of div.page -->

    <!-- Holds UI elements that will be cloned and placed in the main
         page. This block itself is always hidden. -->
    <div id="ui_library">
      <div id="quality" class="quality">
        <span class="name" data-attr="name"></span>
        <span class="value" data-attr="value"></span>
      </div>

      <div id="quality_group" class="quality_group">
        <h2 data-attr="title"></h2>
        <div class="qualities_in_group">
        </div>
      </div>

      <div id="progress_bar" class="progress_bar">
        <span class="name" data-attr="name"></span>
        <span class="value" data-attr="value"></span>
        <div class="progress_bar_track">
          <div class="progress_bar_color" data-attr="width">
          </div>
        </div>
        <span class="left_label" data-attr="left_label"></span>
        <span class="right_label" data-attr="right_label"></span>
      </div>

      <hr id="turn_separator">
    </div>

    <!-- You don't need to have this block here, but it is defined in
         the CSS file as hidden, so it is a good spot to hide content
         you want to load from your game code. See the
         tutorial.game.js file for details of how this is used. -->
    <div id="content_library">
      <div id="s_situations">
        <h1>Situations</h1>
        <p>
          In Undum, all interaction takes place in a situation. You
          can think of it either as a 'Room' in traditional
          interactive fiction (although it is less flexible than
          that), or as a 'Page' in a Choose Your Own Adventure book
          (though it is more flexible than that).
        </p>
        <p>
          At any point, the character is in exactly one situation, and
          that situation is responsible for everything that happens to
          them. Situations are chunks of code that generate the output
          you are reading here. For example, this text was generated
          by the <em>enter</em> method of the 'situations' situation.
        </p>
        <p class='transient'>
          Let's <a href='todo'>move on again</a>.
        </p>
      </div>

      <div id="s_saving">
        <h1>Saving and Loading</h1>
        <p>The only piece of the UI we haven't talked about is the
          'Save' and 'Erase' buttons on the left panel. These are only
          visible if your browser supports client-side data
          storage. Clicking 'Save' stores your game, so you can pick
          it up again later. There is currently no 'Load' button, the
          game loads when the page loads. There is also no way to save
          multiple games, and select which one you want to play. These
          are both things I'd like to change in the future.
        </p>
        <p>
          Potentially your game could generate huge amounts of
          text. And that would be difficult to store client side
          (there are unpredictable limits), especially when we move
          towards having multiple save files. So instead Undum saves
          your character as the list of links you clicked. Loading a
          save-file consists of playing through your game again,
          quickly. This is a beneficial approach for debugging too. It
          means when you're polishing and correcting typos, you can
          save and load the game and scroll through the transcript to
          see your corrections. If we saved the text, your save file
          would have the error in it and you'd have to manually replay
          the game to see the correction.
        </p>
        <p class='transient'>
          Let's return to the <a href='hub'>topic list</a>.
        </p>
      </div>

      <!-- Some situations defined entirely in the HTML -->
      <div id="hub" class="situation" data-choices="#topic"
           data-option-text="View Topic List">
        <h1 class="transient">Topics</h1>
        <p class="transient">Choose a topic to find out about next. If
          in doubt, go through the topics in order.</p>
      </div>

      <div id="implicit" class="situation" data-tags="topic"
           data-heading="Implicit Choices" data-display-order="7"
           data-choices="#example">
        <p>When you're writing an Undum game, you often need certain
          options to be available only when certain conditions hold. You
          might have an option to remove a secret panel in a haunted
          house, but that should only be visible if the character knows
          where it is. If options are available in lots of situations, it
          can be very difficult to keep track of what options are
          allowed, and to produce just the right list of choices.</p>
        <p>To help with this, Undum can generate a list of situation
          links for you. It does this in three steps. Firstly, each
          situation can be given one or more tags, this allows you to
          easily ask for links to all situations with the 'in-hallway'
          tag, for example. Secondly, situations can have
          a <em>canView</em> method, which gets to decide whether that
          situation should appear. That method can look at the
          current state of the character to decide whether to appear
          or not. Thirdly, <em>SimpleSituation</em>s have a <em>choices</em>
          option. If it is set to one or more tags, it handles the building
          of the choice list.</p>
        <p>You've seen this already in the topic list. The topic list
          is generated automatically. All of the situations in the topic
          list are always available, however.
          <span class="transient">So here is an example of
          automatic options that may change:</span></p>
      </div>

      <div id="example-choices" class="situation" data-choices="#example">
        <p class="transient">You can return to the
          <a href='hub'>Topic List</a> or choose another option from
          this example:</p>
      </div>
    </div>

    <!-- Load the libraries we depend on -->
    <script type="text/javascript" src="media/js/jquery-2.1.3.min.js"></script>
    <script type="text/javascript" src="media/js/undum.js"></script>

    <!-- Change the name of this file. It is your main game file. -->
    <script type="text/javascript"
            src="media/games/tutorial/tutorial.game.en.js"></script>
  </body>
</html>
