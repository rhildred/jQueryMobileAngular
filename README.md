#[JQuery mobile and Angular](https://github.com/rhildred/jQueryMobileAngular)

In a previous experience, I felt that I had to do some unnatural things to make these libraries play well together. Now I am not sure if it was suspiciousness, or if the libraries have improved. One of the things that I like about jQuery Mobile, Angular and Twitter bootstrap is the way that they are declarative. In this simple example I have added the dependencies:

```

<head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.css" />
    <script src="https://code.jquery.com/jquery-1.11.2.min.js"></script>
    <script src="https://code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.js"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js"></script>
    <script src="cordova.js"></script>
</head>

```

I made 2 pages:

```

<body ng-app="">
    <!-- Start of first page: #one -->
    <div data-role="page" id="one">
        <div data-role="header">
            <h1>One</h1>
        </div>
        <div data-role="content">
            this is page 1<br />
            <a href="#two" data-role="button">Next</a>
        </div>
        <div data-role="footer">
            <h1>One</h1>
        </div>
    </div>
    <div data-role="page" id="two">
        <div data-role="header">
            <h1>Two</h1>
        </div>
        <div data-role="content">
            this is page 2<br />
        </div>
        <div data-role="footer">
            <h1>Two</h1>
        </div>

    </div>
</body>

```

Finally I put some form controls on page 1. A couple of regular input fields:

```
<div class="ui-field-contain">
    <label for="amount">Amount:</label>
    <input ng-model="amount" id="amount"/>
    <label for="tip">Tip:</label>
    <input ng-model="tip" id="tip" placeholder="%"/>
</div>

```

A flip-switch:

```
<label for="select-based-flipswitch">Select-based:</label>
<select id="select-based-flipswitch" data-role="flipswitch" ng-model="switch" ng-init="switch='arrive'">
    <option value="leave">Bye</option>
    <option value="arrive" selected="selected">Hi</option>
</select>

```

And a check-box:

```
<fieldset data-role="controlgroup">
    <legend>Agree to the terms:</legend>
    <input ng-model="agreed" ng-init="agreed=false" type="checkbox" name="checkbox-2" id="checkbox-2" class="custom">
    <label for="checkbox-2">I agree</label>
</fieldset>

```

On the second page, I did a calculation on the tip, and redisplayed the amount.

`{{amount}} with tip your purchase is {{(amount * (1 + tip/100)).toFixed(2)}}`

This seems very natural to me. All, so far, without any imperative code.