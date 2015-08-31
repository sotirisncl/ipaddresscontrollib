ipaddresscontrollib has moved to [GitHub](https://github.com/m66n/ipaddresscontrollib).

Latest Revision: [57 (13-Mar-12)](http://code.google.com/p/ipaddresscontrollib/source/list)

![http://ipaddresscontrollib.googlecode.com/svn/images/TestIPAddressControl.png](http://ipaddresscontrollib.googlecode.com/svn/images/TestIPAddressControl.png)

## Introduction ##

Why didn't Microsoft include an IP address control in the stock toolbox for Visual Studio .NET? I needed something similar to the MFC `CIPAddressCtrl` class in a C# application recently, and was forced to roll my own. I tried to mimic the behavior of `CIPAddressCtrl` using C#, and hopefully I've succeeded.

If you need a C# IPv6 address control or a C# MAC address control, take a look at [this project](http://flexfieldcontrollib.googlecode.com).

## Background ##

`IPAddressControl` is a `ContainerControl` that aggregates four specialized `TextBox` controls of type `FieldCtrl` and three specialized `Control`s of type `DotCtrl`.

![http://ipaddresscontrollib.googlecode.com/svn/images/close_up.gif](http://ipaddresscontrollib.googlecode.com/svn/images/close_up.gif)

The `FieldCtrl`s do some validation and keyboard filtering in addition to standard `TextBox` behavior. The `DotCtrl`s do nothing but draw a dot.


## Using The Code ##

Once the library containing `IPAddressControl` (_IPAddressControlLib.dll_) is built, add the control to the Toolbox in Visual Studio. From the Toolbox, just drag the control onto a form and you're ready to go.

NB: When using this code with .NET Framework 4, the WinForms application should target ".NET Framework 4" rather than the default ".NET Framework 4 Client Profile."

The interface to `IPAddressControl` is very simple.

#### Public Instance Properties ####

  * `AnyBlank`: Gets whether any fields in the control are blank.
  * `AutoHeight`: Gets or sets a value indicating whether the control is sized according to the current font and border. Default value is `true`.
  * `Blank`: Gets a value indicating whether all of the fields in the control are empty.
  * `BorderStyle`: Gets or sets the border style of the control. Default value is `BorderStyle.Fixed3D`.
  * `IPAddress`: Gets or sets an `IPAddress` representing the contents of the fields. (VS2010 only)
  * `ReadOnly`: Gets or sets a value indicating if the control is read-only.

#### Public Instance Methods ####

  * `Clear`: Clears the contents of the control.
  * `GetAddressBytes`: Returns an array of `byte`s representing the contents of the fields, index 0 being the leftmost field.
  * `SetAddressBytes`: Sets the values of the fields using an array of `byte`s, index 0 being the leftmost field.
  * `SetFieldFocus`: Sets the keyboard focus to the specified field in the control.
  * `SetFieldRange`: Sets the lower and higher range of a specified field in the control.

The above properties and methods are in addition to the stock properties and methods of `UserControl`. Stock properties such as `Text`, `Enabled`, and `Font`, as well as stock methods such as `ToString()` work as expected.

Client code can register a handler for the public event, `FieldChangedEvent`, to be notified when any text in the fields of the control changes.

Note that `Text` and `ToString()` may not return the same value. If there are any empty fields in the control, `Text` will return a value that will reflect the empty fields. `ToString()` will fill in any empty field with that field's `RangeLower` value. Also, if you are using the control to create an `IPAddress`, you can easily do so using this control's `GetAddressBytes()` method:

```
   IPAddress ipAddress = new IPAddress( ipAddressControl.GetAddressBytes() );
```

Update: The VS2010 version of this code adds `IPAddress` property that renders the above unnecessary.

Copyright (c) Michael Chapman. All rights reserved.