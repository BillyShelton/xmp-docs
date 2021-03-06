# `<xmod:DeleteImage>`

The DeleteImage tag renders as a clickable image at run-time. It is used to execute the `<DeleteCommand>` of its parent `<xmod:Template>`.

## Syntax
```html
<xmod:DeleteImage
    AlternateText="string"
    BackColor="color name|#dddddd"
    BorderColor="color name|#dddddd"
    BorderStyle="NotSet|None|Dotted|Dashed|Solid|Double|Groove|Ridge| Inset|Outset"
    BorderWidth="size"
    CssClass="string"
    Font-Bold="True|False"
    Font-Italic="True|False"
    Font-Names="string"
    Font-Overline="True|False"
    Font-Size="string|Smaller|Larger|XX-Small|X-Small|Small|Medium| Large|X-Large|XX-Large"
    Font-Strikeout="True|False"
    Font-Underline="True|False"
    ForeColor="color name|#dddddd"
    Height="size"
    ImageAlign="NotSet|Left|Right|Baseline|Top|Middle|Bottom|AbsBottom|AbsMiddle|TextTop"
    ImageUrl="url"
    OnClientClick="javascript"
    Style="string"
    ToolTip="string"
    Visible="True|False"
    Width="size" >

      <Parameter Name="string" Value="string" Alias="string" Datatype="boolean|string|int32"/>
      <Parameter Name="string" Value="string" Alias="string" Datatype="boolean|string|int32"/>
      ...additional parameters as needed ...

</xmod:DeleteImage> 
```

## Remarks

*   **Usage**: The XMod Pro Delete controls work in conjunction with the `<DeleteCommand>` tag of the `<xmod:Template>` tag. Typically, the delete command will include one or more `<parameter>` tags that identify which record(s) should be deleted. The delete control should use the same parameter names and fill them with valid values, typically from the current record. That's why delete controls are typically found in `<ItemTemplate>` and `<AlternatingItemTemplate>` tags.  

*   **AlternateText**: Use this attribute's value will be used as the image's "alt" text. The "alt" text is generally used by screen reader software used by visually impaired users to identify the content of an image. It may also be used by search engines.  

*   **BackColor**: Color of the background of the control.  

*   **BorderColor**: Color of the border around the control.  

*   **BorderStyle**: Style of the border around the control.  

*   **BorderWidth**: Width of the border around the control, specified in [units](../unit-types.md)

*   **CssClass**: Name of the Cascading Style Sheets (CSS) class used to style this control.  

*   **Font Properties**: A series of attributes such as font-bold, font-size, etc. that allow you to control how the text in the control is displayed. [More](../font-properties.md)

*   **ForeColor**: Sets the foreground color (typically the color of the text) of the control.  

*   **Height**: Height of the control, specified in [units](../unit-types.md).  

*   **ImageAlign**: This attribute determines how the image will be aligned with respect to the other elements in its context.  

*   **ImageUrl**: Specify a URL to the image. You may use the tilde (~) character to represent the application's root directory. For instance: ImageUrl="~/images/myimage.gif" might map to "/dnntestsite/images/myimage.gif" on your localhost development machine and "/images/myimage.gif" on your production server.  

*   **OnClientClick**: Should you wish to perform some action on the client when the control is clicked, add your Javascript function call or script in this attribute. If your script returns _false_ the control will not perform its normal processing. If you return true then the control will perform its normal processing.  

*   **Style**: Same as the HTML style attribute. It allows you to apply CSS styling to the control (e.g. `color: red; border: solid 1px black;`).  

*   **ToolTip**: In browsers that support it, sets the text to display when the mouse pointer hovers over the control.  

*   **Visible**: Determines if the control is visible (true) or hidden (false).  

*   **Width**: Width of the control in [units](../unit-types.md).

## Example
```html {23-27}
<div>
  <table width="100%">
    <tr>
      <td width="250" valign="top">

        <!-- EMPLOYEES TEMPLATE -->

        <xmod:Template Id="Employees">
          <ListDataSource CommandText="SELECT * FROM XMPDemo_Employees WHERE DepartmentId = @DepartmentId"> 
            <Parameter Name="DepartmentId" Alias="DepartmentId"/>
          </ListDataSource>
          <DeleteCommand CommandText="DELETE FROM XMPDemo_Employees WHERE EmployeeId = @EmpID">
            <Parameter Name="EmployeeId" Alias="EmpID" />
          </DeleteCommand>

          <HeaderTemplate>
            <p>Employees</p>
          </HeaderTemplate>
          
          <ItemTemplate>
            <div style="text-align: middle;">
              <strong>[[FirstName]] [[LastName]]</strong>
              <xmod:DeleteImage AlternateText="Delete Employee" 
                    OnClientClick="return confirm('Are you sure you want to delete this employee?');" 
                    ImageUrl="~/images/delete.gif">
                <Parameter Name="EmployeeId" Alias="EmpID" 
                           Value='[[EmployeeId]]' Datatype="int32" />
              </xmod:DeleteImage>
            </div>
          </ItemTemplate>
        
        </xmod:Template>
      </td>
    </tr>
  </table>
</div>  
```