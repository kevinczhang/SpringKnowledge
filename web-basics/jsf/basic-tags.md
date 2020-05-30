# Basic Tags

JSF provides a standard HTML tag library. These tags get rendered into corresponding html output.

For these tags you need to use the following namespaces of URI in html node.

```markup
<html xmlns = "http://www.w3.org/1999/xhtml" 
    xmlns:h = "http://java.sun.com/jsf/html">
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
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_inputtext_tag.htm">h:inputText</a>
        </p>
        <p>Renders a HTML input of type=&quot;text&quot;, text box.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_inputsecret_tag.htm">h:inputSecret</a>
        </p>
        <p>Renders a HTML input of type=&quot;password&quot;, text box.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_inputtextarea_tag.htm">h:inputTextarea</a>
        </p>
        <p>Renders a HTML textarea field.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_inputHidden_tag.htm">h:inputHidden</a>
        </p>
        <p>Renders a HTML input of type=&quot;hidden&quot;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_selectbooleancheckbox_tag.htm">h:selectBooleanCheckbox</a>
        </p>
        <p>Renders a single HTML check box.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_selectmanycheckbox_tag.htm">h:selectManyCheckbox</a>
        </p>
        <p>Renders a group of HTML check boxes.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">7</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_selectoneradio_tag.htm">h:selectOneRadio</a>
        </p>
        <p>Renders a single HTML radio button.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">8</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_selectonelistbox_tag.htm">h:selectOneListbox</a>
        </p>
        <p>Renders a HTML single list box.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_selectmanylistbox_tag.htm">h:selectManyListbox</a>
        </p>
        <p>Renders a HTML multiple list box.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">10</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_selectonemenu_tag.htm">h:selectOneMenu</a>
        </p>
        <p>Renders a HTML combo box.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">11</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_outputtext_tag.htm">h:outputText</a>
        </p>
        <p>Renders a HTML text.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">12</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_outputformat_tag.htm">h:outputFormat</a>
        </p>
        <p>Renders a HTML text. It accepts parameters.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">13</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_graphicimage_tag.htm">h:graphicImage</a>
        </p>
        <p>Renders an image.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">14</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_outputstylesheet_tag.htm">h:outputStylesheet</a>
        </p>
        <p>Includes a CSS style sheet in HTML output.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">15</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_outputscript_tag.htm">h:outputScript</a>
        </p>
        <p>Includes a script in HTML output.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">16</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_commandbutton_tag.htm">h:commandButton</a>
        </p>
        <p>Renders a HTML input of type=&quot;submit&quot; button.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">17</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_link_tag.htm">h:Link</a>
        </p>
        <p>Renders a HTML anchor.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">18</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_commandlink_tag.htm">h:commandLink</a>
        </p>
        <p>Renders a HTML anchor.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">19</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_outputlink_tag.htm">h:outputLink</a>
        </p>
        <p>Renders a HTML anchor.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">20</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_panelgrid_tag.htm">h:panelGrid</a>
        </p>
        <p>Renders an HTML Table in form of grid.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">21</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_message_tag.htm">h:message</a>
        </p>
        <p>Renders message for a JSF UI Component.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">22</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_messages_tag.htm">h:messages</a>
        </p>
        <p>Renders all message for JSF UI Components.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">23</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_param_tag.htm">f:param</a>
        </p>
        <p>Pass parameters to JSF UI Component.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">24</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_attribute_tag.htm">f:attribute</a>
        </p>
        <p>Pass attribute to a JSF UI Component.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">25</td>
      <td style="text-align:left">
        <p><a href="https://www.tutorialspoint.com/jsf/jsf_setpropertyactionlistener_tag.htm">f:setPropertyActionListener</a>
        </p>
        <p>Sets value of a managed bean&apos;s property.</p>
      </td>
    </tr>
  </tbody>
</table>

