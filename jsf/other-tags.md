# Other tags

## Facelets Tags

JSF provides special tags to create common layout for a web application called facelets tags. These tags provide flexibility to manage common parts of multiple pages at one place. For these tags, you need to use the following namespaces of URI in html node.

```markup
<html  
   xmlns = "http://www.w3.org/1999/xhtml"  
   xmlns:ui = "http://java.sun.com/jsf/facelets">
```

<table>
  <thead>
    <tr>
      <th style="text-align:left">S.No</th>
      <th style="text-align:left">Tag &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_templates_tag.htm">Templates</a>
        </p>
        <p>We&apos;ll demonstrate how to use templates using the following tags</p>
        <ul>
          <li>&lt;ui:insert&gt;</li>
          <li>&lt;ui:define&gt;</li>
          <li>&lt;ui:include&gt;</li>
          <li>&lt;ui:composition&gt;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_parameters_tag.htm">Parameters</a>
        </p>
        <p>We&apos;ll demonstrate how to pass parameters to a template file using
          the following tag</p>
        <ul>
          <li>&lt;ui:param&gt;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_custom_tag.htm">Custom</a>
        </p>
        <p>We&apos;ll demonstrate how to create custom tags</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_remove_tag.htm">Remove</a>
        </p>
        <p>We&apos;ll demonstrate capability to remove JSF code from generated HTML
          page</p>
      </td>
    </tr>
  </tbody>
</table>## Convertor Tags

JSF provides inbuilt convertors to convert its UI component's data to object used in a managed bean and vice versa. For example, these tags can convert a text into date object and can validate the format of input as well. For these tags, you need to use the following namespaces of URI in html node.

```text
<html 
   xmlns = "http://www.w3.org/1999/xhtml" 
   xmlns:f = "http://java.sun.com/jsf/core">
```

<table>
  <thead>
    <tr>
      <th style="text-align:left">S.No</th>
      <th style="text-align:left">Tag &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_convertnumber_tag.htm">f:convertNumber</a>
        </p>
        <p>Converts a String into a Number of desired format</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_convertdatetime_tag.htm">f:convertDateTime</a>
        </p>
        <p>Converts a String into a Date of desired format</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_customconvertor_tag.htm">Custom Convertor</a>
        </p>
        <p>Creating a custom convertor</p>
      </td>
    </tr>
  </tbody>
</table>## Validator Tags

JSF provides inbuilt validators to validate its UI components. These tags can validate the length of the field, the type of input which can be a custom object. For these tags you need to use the following namespaces of URI in html node.

```text
<html 
   xmlns = "http://www.w3.org/1999/xhtml" 
   xmlns:f = "http://java.sun.com/jsf/core">
```

<table>
  <thead>
    <tr>
      <th style="text-align:left">S.No</th>
      <th style="text-align:left">Tag &amp; Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_validatelength_tag.htm">f:validateLength</a>
        </p>
        <p>Validates the length of a string</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_validatelongrange_tag.htm">f:validateLongRange</a>
        </p>
        <p>Validates the range of a numeric value</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_validatedoublerange_tag.htm">f:validateDoubleRange</a>
        </p>
        <p>Validates the range of a float value</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_validateregex_tag.htm">f:validateRegex</a>
        </p>
        <p>Validates JSF component with a given regular expression</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_customvalidator_tag.htm">Custom Validator</a>
        </p>
        <p>Creates a custom validator</p>
      </td>
    </tr>
  </tbody>
</table>