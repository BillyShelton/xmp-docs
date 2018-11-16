# <Validate type="required">





The Validate tag whose type is set to "required" is referred to as a Required Field Validator and is used to ensure the user provides some input for a given control.



## Syntax

<div class="Code">`<Validate`  
``    BackColor="_color name_|#dddddd"  
    BorderColor="_color name_|#dddddd"  
    BorderStyle="**NotSet**|None|Dotted|Dashed|Solid|Double|Groove|Ridge| Inset|Outset"  
    BorderWidth="_size_"  
    CssClass="_string_"  
    Display="Static|**Dynamic**"  
    EnableClientScript="**True**|False"`  
`    Font-Bold="True|**False**"  
    Font-Italic="True|**False**"  
    Font-Names="_string_"  
    Font-Overline="True|**False**"  
    Font-Size="_string_|Smaller|Larger|XX-Small|X-Small|Small|Medium| Large|X-Large|XX-Large"  
    Font-Strikeout="True|**False**"  
    Font-Underline="True|**False**"  
    ForeColor="_color name_|#dddddd"  
    Height="_size_"  
    Message="_string_"  
    Target="_string_"  
    Text="_string_"  
    Type="Required"  
    Width="_size_"``  
`/> `</div>

 

## Remarks

The required field validator is one type of the `<Validate>` tag. When the "type" attribute is set to **Required**, the control prevents the form from being submitted if its associated control does not have a value. You associate a control with the <validate> tag by setting its "target" attribute to the ID of the control you wish to validate. The "message" attribute is the text that will be displayed to the user when validation fails. If you are using the `<ValidationSummary>` tag, then you can also supply a "text" attribute. When validation fails, the "text" will be displayed where your `<Validate>` tag is and the "message" will be displayed in the `<ValidationSummary>`. The "display" attribute determines if the the `<Validate>` tag will reserve space for its message in the page layout - typically resulting in blank space in your form -or whether it will dynamically display allocate the space for the message when validation fails. The `<Validate>` tag defaults to **Dynamic** display.



*   **BackColor**: Color of the background of the control.  

*   **BorderColor**: Color of the border around the control.  

*   **BorderStyle**: Style of the border around the control. Defaults to NotSet.  

*   **BorderWidth**: Width of the border around the control, specified in [units.  

    ](../unit-types.md)
*   **CssClass**: Name of the Cascading Style Sheets (CSS) class used to style this control.  

*   **Display**: This attribute determines if the <span style="font-family: monospace;"><Validate></span> tag will reserve space for its message in the page layout - typically resulting in blank space in your form -or whether it will dynamically allocate the space for the message when validation fails. Defaults to **Dynamic** display.  

*   **EnableClientScript**: Use the EnableClientScript property to specify whether client-side validation is enabled. Defaults to **True**.  

*   **Font Properties**: A series of attributes such as font-bold, font-size, etc. that allow you to control how the text in the control is displayed. [More  

    ](../font-properties.md)
*   **ForeColor**: Sets the foreground color (typically the color of the text) of the control.  

*   **Height**: Height of the control, specified in [units](../unit-types.md).  

*   **Message**: This is the text that will be displayed to the user, when validation fails. If you are using the <span style="font-family: monospace;" xmlns="http://www.w3.org/1999/xhtml"><ValidationSummary</span>, then this is the message that will be displayed in the <span style="font-family: monospace;" xmlns="http://www.w3.org/1999/xhtml"><ValidationSummary></span> when validation fails.  

*   **Target**: Set this attribute to the ID of the control you wish to validate.  

*   **Text**: If you are using the `<ValidationSummary>` tag, then you can also supply a "text" attribute. When validation fails, the "text" will be displayed where your `<Validate>` tag is and the "message" will be displayed in the `<ValidationSummary>`.  

*   **Type**: When the "type" attribute is set to **Required**, the control prevents the form from being submitted if its associated control does not have a value.  

*   **Width**: Width of the control in [units](../unit-types.md).  

## Example

<div class="Code" xmlns="">`<AddForm>`  
`  <SubmitCommand CommandText="INSERT INTO Users(FirstName, LastName) VALUES(@FirstName, @LastName)" />`  
`    <table>`  
`      <tr>`  
`        <td>`  
`          <Label For="txtFirstName" Text="FirstName" />`  
`          <TextBox Id="txtFirstName" DataField="FirstName" DataType="string" />`  
`<span style="color: #ff0000;"><Validate Type="required" Target="txtFirstName" Message="You must enter a First Name" /></span>`  
`        </td>`  
`      </tr>`  
`      <tr>`  
`        <td>`  
`          <Label For="txtLastName" Text="Last Name" />`  
`          <TextBox Id="txtLastName" DataField="LastName" DataType="string" />`  
`        </td>`  
`      </tr>`  
`      <tr>`  
`        <td colspan="2">`  
`          <AddButton Text="Add" />&nbsp;<CancelButton Text="Cancel" />`</div>

<div class="Code" xmlns="">`          <ValidationSummary />`  
`        </td>`  
`      </tr>`  
`    </table>`  
`</AddForm>`</div>

