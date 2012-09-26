---
layout: design-pattern
title: Forms
status: draft
---

The 'form' mixin provides a configurable framework for most basic form layouts.

Use it in your Sass like this: `.form-example-1 { @include form }`

<div class="side-by-side">
  <div>
    <h1>Example 1</h1>
<div class="pattern-example">
  <div class="inner">
    <form class="form-example-1">
    <p class="group">
      <label>Label one</label>
      <input type="text">
    </p>
    <p class="group">
      <label>Label two</label>
      <input type="text">
    </p>
    <p class="group">
      <label>Label three</label>
      <input type="text">
    </p>
    </form>
  </div>
</div> 
  </div>
  <div>
  <h1>HTML</h1>
<pre><code>
&lt;form class="form-example-1"&gt;
  &lt;p class="group"&gt;
    &lt;label&gt;Label 1&lt;/label&gt;
    &lt;input type="text"&gt;
  &lt;/p&gt;
  &lt;p class="group"&gt;
    &lt;label&gt;Label 2&lt;/label&gt;
    &lt;input type="text"&gt;
  &lt;/p&gt;
  &lt;p class="group"&gt;
    &lt;label&gt;Label 3&lt;/label&gt;
    &lt;input type="text"&gt;
  &lt;/p&gt;
&lt;/form&gt;

</code></pre>
  </div>
</div>


<h2>Arguments</h2>
<p>The form mixin accepts the following arguments:</p>
<p><code>$label-alignment</code> top, left or right. Default is top.</p>
<p><code>$label-width</code> a value in em. Default is 8em.</p>
<p><code>$legend-colour</code> a colour value or variable. Default is $charcoal-grey.</p>

# Example 2: Contact form

The following example incorporates most of the basic form elements. You can toggle through the different label alignment options to see
the effect it has.

<div class="pattern-example">

<pre><code class="class-toggle" data-for="form-example-2" >@include form(<span class="option selected">top</span>|<span class="option">left</span>|<span class="option">right</span>, 7.5em, $mellow-red)</code></pre>

  <div class="inner">

    <form id="form-example-2" class="top">
      <fieldset>
        <legend>Name</legend>
        <p class="group">
          <label>Title</label>
          <select>
            <option value="Mr">Mr.</option>
            <option value="Mrs">Mrs.</option>
            <option value="Miss">Miss</option>
            <option value="Ms.">Ms.</option>
            <option value="Dr.">Dr.</option>
            <option value="Other">Other</option>
          </select>
        </p>
        <p class="group">
          <label>First name <abbr title="Mandatory">*</abbr></label>
          <input type="text" class="name">
        </p>
        <p class="group">
          <label>Last name <abbr title="Mandatory">*</abbr></label>
          <input type="text" class="name">
        </p>
      </fieldset>
      <fieldset>
        <legend>Email address</legend>
        <p class="group">
          <label>Enter email <abbr title="Mandatory">*</abbr></label>
          <input type="text" class="email">
        </p>
        <p class="group">
          <label>Confirm email <abbr title="Mandatory">*</abbr></label>
          <input type="text" class="email">
        </p>
      </fieldset>
      <fieldset>
        <legend>Telephone number</legend>
        <p class="group">
          <label>Telephone</label>
          <input type="text" class="telephone">
          <span class="help">Include your country code</span>
        </p>
      </fieldset>
      <fieldset>
        <legend>Postal address</legend>
        <p class="group">
          <label>Street</label>
          <input type="text" class="street">
        </p>
        <p class="group">
          <label class="visuallyhidden">Street line two</label>
          <input type="text" class="street">
        </p>
        <p class="group">
          <label>Town/City</label>
          <input type="text" class="town">
        </p>
        <p class="group">
          <label>Postcode</label>
          <input type="text" class="postcode">
        </p>
      </fieldset>
      <fieldset>
        <legend>Biography</legend>
        <p class="group">
          <label for="biography">Write a few short words about yourself</label>
          <textarea name="biography" class="big"></textarea>
        </p>
        <p class="option group">
          <label><input type="checkbox"> Make this biography public</label>
        </p>
      </fieldset>
      <fieldset>
        <legend>I am interested in</legend>
        <ul class="option group">
          <li><label><input type="checkbox"> Job offers</label></li>
          <li><label><input type="checkbox"> Networking</label></li>
          <li><label><input type="checkbox"> Business opportunities</label></li>
        </ul>
      </fieldset>  
      <fieldset>
        <legend>I prefer to be contacted by</legend>
        <ul class="option group">
          <li><label><input type="radio" name="preferred-contact" checked> Email</label></li>
          <li><label><input type="radio" name="preferred-contact"> Telephone</label></li>
          <li><label><input type="radio" name="preferred-contact"> Post</label></li>
        </ul>
      </fieldset>
      <p class="action group">
        <button class="button" type="submit">Submit form</button>
      </p>
    </form>

  </div>
</div>

* * *

# Rationale

## Text input fields

* Light grey background: To make them stand out equally on a white page or coloured panel
* Inset border style: By convention people type into 'holes' cut into the interface

## Label positioning

The framework provides support for top, left or right alignment because there are valid cases for the use of all three. The table below (from a [great article on form design](http://uxdesign.smashingmagazine.com/2011/11/08/extensive-guide-web-form-usability/) in Smashing Magazine) outlines the relative advantages of each approach:

|-----------------------------------|--------------|-------------------|---------------|
|                                   | Top          | Right             | Left          |
|-----------------------------------|--------------|-------------------|---------------|
| Speed of completion               | Fastest      |                   | Slowest       |
|-----------------------------------|--------------|-------------------|---------------|
| Horizontal space                  | Least        |                   | Most          |
|-----------------------------------|--------------|-------------------|---------------|
| Vertical space                    | Most         |                   | Least         |
|-----------------------------------|--------------|-------------------|---------------|
| Label text space                  | Most         |                   | Least         |
|-----------------------------------|--------------|-------------------|---------------|
| Proximity to input                | Closest      |                   | Least close   |
|-----------------------------------|--------------|-------------------|---------------|
| User eye movement                 | Down         | Down + right      | Down + right  |
|-----------------------------------|--------------|-------------------|---------------|
| Time to move from label to input  | 50ms         | 240ms             | 500ms         |
|-----------------------------------|--------------|-------------------|---------------|
| Ideal for                         | Simple forms | Less simple forms | Complex forms |
|-----------------------------------|--------------|-------------------|---------------|




<script>
  $(function() {

    // Style toggle for pattern examples
    // Takes the text of the clicked 'option' and assigns it as
    // a class to the element named in the 'data-for' attribute
    $('.class-toggle .option').click(function(){
      $('.class-toggle .option').removeClass('selected');
      $(this).addClass('selected');
      var selectedClass = $(this).text();
      var selectedElement = "#" + $(this).parents('.class-toggle').data("for");
      $(selectedElement).removeClass().addClass(selectedClass);
      return false;
    });



  });
</script>