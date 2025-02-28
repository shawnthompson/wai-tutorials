---
title: Validating Input
permalink: /tutorials/forms/validation/
ref: /tutorials/forms/validation/
lang: en

description:
image: /content-images/wai-tutorials/forms/social.png
github:
  branch: 'master-2.0'
  repository: w3c/wai-tutorials
  path: 'content/forms/validation.md'

resource:
  ref: /tutorials/forms/
navigation:
  previous: /tutorials/forms/instructions/
  next: /tutorials/forms/notifications/


wcag_success_criteria:
  - 3.3.1
  - 3.3.4
wcag_techniques:
  - G164
  - G98
  - G83
  - G85
  - G155
  - G168

metafooter: true
last_updated: 2019-07-27
editors:
  - Eric Eggert: "https://www.w3.org/People/yatil/"
  - Shadi Abou-Zahra: "https://www.w3.org/People/shadi/"
contributors:
  - The Web Content Accessibility Guidelines Working Group (<a href="https://www.w3.org/WAI/GL/">WCAG WG</a>)
  - the Education and Outreach Working Group (<a href="https://www.w3.org/WAI/EO/">EOWG</a>)
support: Developed with support from the <a href="https://www.w3.org/WAI/ACT/">WAI-ACT project</a>, co-funded by the <strong>European Commission <abbr title="Information Society Technologies">IST</abbr> Programme</strong>.
---

In addition to providing instructions, validate user input to help users avoid mistakes. HTML5 defines a range of built-in functionality to validate common types of input, such as email addresses and dates. In some situations, such as validating custom controls or supporting legacy browsers, additional scripting may be necessary to validate user input.

Custom validation needs to notify users in an accessible way as described in the [User Notifications](/tutorials/forms/notifications/) part of this tutorial. Client-side validation alone does not ensure security; therefore data needs to be validated on the server-side as well.

## Validating required input
{:.newex}

Forms frequently include required input that needs to be clearly identified using labels. Also, the `required` attribute can be added to form controls, to programmatically indicate that they are required. Most current web browsers support this attribute and will communicate missing required input to the user, using standard web browser dialog mechanisms. These dialogs are expected to respect the settings and preferences of the user in the web browser (and operating system), such as default font-size, colors, and language.

In the example below, the `required` attribute is added to the input field. If your web browser supports HTML5, it will not allow you to submit the form without entering text into the input field. Instead, it will display a message that is generated by the web browser itself.

Note that the label also displays “(required)”, to inform users that don’t use assistive technology or use older web browsers that do not support the HTML5 `required` attribute.

{::nomarkdown}
{% include box.html type="start" title="Example" class="example" %}
{:/}

<form method="post" action="../../beyond/">
	<div>
		<label for="name">Name (required): </label> <input type="text" name="name" id="name" required aria-required="true">
		<input type="submit" value="Submit">
	</div>
</form>

{::nomarkdown}
{% include box.html type="end" %}
{:/}

{::nomarkdown}
{% include box.html type="start" title="Code Snippet" class="example" %}
{:/}

~~~ html
<label for="name">Name (required): </label>
<input type="text" name="name" id="name" required aria-required="true">
~~~

{::nomarkdown}
{% include box.html type="end" %}
{:/}

{::nomarkdown}
{% include box.html type="start" title="Note" class="simple notes" %}
{:/}

{% include ednote.html note="Remove this note, remove ARIA-required in the example" %}

**Note:** The `aria-required` attribute informs assistive technologies about required controls so that they are appropriately announced to the users (as opposed to validating the input). Most current web browsers automatically set its value to `true` when the HTML5 `required` attribute is present. In this example, it is provided redundantly to support web browsers that don’t communicate the `required` attribute to assistive technology.

{::nomarkdown}
{% include box.html type="end" %}
{:/}

## Validating common input
{:.newex}

HTML5 also provides input types for other data, including `email`, `url`, `number`, `range`, `date`, or `time`. Most current web browsers support these features and handle input validation. Also, HTML5 validation helps users inputting data by providing specific controls, such as date pickers and custom on-screen keyboards. HTML5 input types are displayed as simple `text` input fields in older web browsers that do not support these HTML5 features.

The example below shows these HTML5 input types in action. Depending on your web browser, the “Range” input field will be displayed as a slider control to help users provide input more easily. Similarly, the “Number” input field may be displayed with buttons to increase or decrease the number incrementally. Input errors, such as an incorrect email address, will be indicated using the web browser dialogs as in the previous example.

{::nomarkdown}
{% include box.html type="start" title="Example" class="example" %}
{:/}

<form method="post" action="../../beyond/" id="valform">
	<div>
		<div><label for="email">Email: </label></div>
		<div><input type="email" name="email" id="email"></div>
	</div>
	<div>
		<div><label for="url">Website: </label></div>
		<div><input type="url" name="url" id="url"></div>
	</div>
	<div>
		<div><label for="number">Number: </label></div>
		<div><input type="number" name="number" id="number" min="0" max="100" step="10" value="0"></div>
	</div>
	<div>
		<div><label for="range">Range: </label></div>
		<div><input type="range" name="range" id="range" min="0" max="100" step="10" value="0"></div>
	</div>
	<div>
		<div><label for="date">Date: </label></div>
		<div><input type="date" name="date" id="date"></div>
	</div>
	<div>
		<div><label for="time">Time: </label></div>
		<div><input type="time" name="time" id="time"></div>
	</div>
	<div>
		<div></div>
		<div><input type="submit" value="Submit"></div>
	</div>
</form>

<style>
	#valform {display:table}
	#valform>div {display:table-row}
	#valform>div>div {display:table-cell; padding: .1em;}
</style>

{::nomarkdown}
{% include box.html type="end" %}
{:/}
{::nomarkdown}
{% include box.html type="start" title="Code Snippet" class="example" %}
{:/}

~~~ html
<div>
	<label for="email">Email: </label>
	<input type="email" name="email" id="email">
</div>
<div>
	<label for="url">Website: </label>
	<input type="url" name="url" id="url">
</div>
<div>
	<label for="number">Number: </label>
	<input type="number" name="number" id="number" min="0" max="100" step="10" value="0">
</div>
<div>
	<label for="range">Range: </label>
	<input type="range" name="range" id="range" min="0" max="100" step="10" value="0">
</div>
<div>
	<label for="date">Date: </label>
	<input type="date" name="date" id="date">
</div>
<div>
	<label for="time">Time: </label>
	<input type="time" name="time" id="time">
</div>
~~~

{::nomarkdown}
{% include box.html type="end" %}
{:/}

{::nomarkdown}
{% include box.html type="start" title="Note" class="simple notes" %}
{:/}

**Note:** Several of these HTML5 input types have additional parameters to help limit and validate the input. They include:

* `maxlength` defines the maximum length of a text field.
* `min` and `max` define the minimum and maximum of `number` and `range` fields.
* `steps` defines in what steps number and range fields can be incremented and decremented.

{::nomarkdown}
{% include box.html type="end" %}
{:/}

## Validating patterned input
{:.newex}

The HTML5 `pattern` attribute allows the use of [regular expressions](https://www.w3.org/TR/html/forms.html#the-pattern-attribute) to specify custom formats for the input. This is useful for specific types of data patterns such as telephone numbers, postal codes, and serial numbers.

### Car license plate numbers
{:.ex}

In the example below, the `pattern` attribute of the `input` element specifies a particular format that matches car license plate (registration) numbers in Germany. The required pattern consists of one to three letters (for the city where the car is registered), followed by a space, two to four random letters, another space, then one to four random numbers.

{::nomarkdown}
{% include box.html type="start" title="Example" class="example" %}
{:/}

<form method="post" action="../../beyond/">
	<div>
		<label for="license">German License Plate (CCC XXXX 9999):</label> <input type="text" id="license" pattern="[A-ZÖÄÜ]{1,3} [A-Z]{2,4} [0-9]{1,4}" />
	</div>
	<div>
	</div>
</form>

{::nomarkdown}
{% include box.html type="end" %}
{:/}
{::nomarkdown}
{% include box.html type="start" title="Code Snippet" class="example" %}
{:/}

~~~ html
<div>
	<input type="text" id="license"
		pattern="[A-ZÖÄÜ]{1,3} [A-Z]{2,4} [0-9]{1,4}"
	>
</div>
~~~

{::nomarkdown}
{% include box.html type="end" %}
{:/}


## Be forgiving of different input formats

Validation should aim to be as accommodating as possible of different forms of input for particular data types. For example, telephone numbers are written with different separators and digit groupings. Your form will be easier to use if it can interpret multiple notations. Also, it is helpful to be liberal with input. For example, postal codes aren't confined to just numbers in some countries, so using an `input` of the type `number` can easily become a problem for many of your website users.

## Client-side validation benefits

In general, client-side validation results in a better user experience and makes resolving validation errors more understandable. It can also reduce network and server load. However, not all web browsers support HTML5, or they may not support your custom validation scripts. Client-side validation can also be easily bypassed, or the data is changed before reaching the server. This means that validation needs to be carried out server-side as well.

## Validation by the user

Where possible, users should be able to check their input and correct it if necessary. This is particularly important for actions that are permanent or otherwise critical, but also when data cannot be automatically checked. For example, providing users with the option to check the postal address that they provided can be useful before a purchase is completed.

### Require user confirmation

Where possible, require user confirmation for irreversible actions, such as permanent deletion of data. Examples include:

* A CMS allows users to delete comments from the trash folder permanently. When this action is initiated, a dialog box is displayed to the user to confirm the action.

* A banking application requires users to confirm transfer transactions by selecting a checkbox labeled “I have checked that the amount I wish to transfer is correct”.

* A shopping website displays a summary of the order, shipping address, and billing information that the user must confirm before the purchasing transaction is completed and the order is placed.

### Provide undo functionality

Where possible, provide mechanisms to undo reversible actions. Examples include:

* A Content Management System (CMS) can delete unwanted comments. Instead of deleting them right away, they are stored in a “trash” folder so that they can be restored.

* A webmail application allows users to “undo” sending an email for a few seconds. This is useful if the user forgot to attach a file or sent the email to the wrong recipient.

* A shopping website lets users cancel purchases up to 24 hours after the order is submitted. The website explains the policy and includes a summary of the policy on the purchase receipt emailed to the user. After 24 hours, the purchase will be shipped to the user and can no longer be canceled.
