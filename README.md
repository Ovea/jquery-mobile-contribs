JQueryMobile contribs
=====================

A - Navigation Events
---------------------

### 1 - Define the eventbus (https://github.com/Ovea/js-eventbus)

    if (myapp.bus == undefined) {
      (function($) {
        myapp.bus = {
          local: new EventBus({
            name: 'EventBus Local'
          })
        };
      })(jQuery);
    }

### 2 - Bridge jquery Mobile with the EventBus

    if (myapp.namesapce == undefined) {
      (function($) {
        window.jqmcontrib.bridge(myapp.bus.local);
      })(jQuery);
    }

### 3 - No you can listen anywhere on your code the JQueryMobile events (pagebeforeshow, pagecreate, pageshow, pagehide) through topics (beforeshow, create, show, hide).

    // Be notified by the creation of the page 'member'
    myapp.bus.local.topic('/event/ui/view/create/member').subscribe(function(page) {
                                                                     r
    }

    // For all pages
    myapp.bus.local.topic('/event/ui/view/create').subscribe(function(page) {

    }

    ....

B - Navigation
--------------

### 1 - Define the eventbus (https://github.com/Ovea/js-eventbus)

    if (myapp.bus == undefined) {
      (function($) {
        myapp.bus = {
          local: new EventBus({
            name: 'EventBus Local'
          })
        };
      })(jQuery);
    }

### 2 - Init Navigation object

    if (app.navigation == undefined) {
      (function($) {
        app.navigation = new window.jqmcontrib.Navigation(myapp.bus.local);
      })(jQuery);
    }

### 3 - Use in your app

    // In which page I am ?
    var page = app.navigation.pageName();

    // Go to external URL and when I come back to my app go to page : myPage
    app.navigation.redirect(external_url, {
      to: myPage
    });

  N.B : The navigation object publish on topic '/event/navigation/restoring'
  when it restore state

    // Change page
    app.navigation.changePage('game');






