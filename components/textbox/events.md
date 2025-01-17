---
title: Events
page_title: Textbox for Blazor | Events
description: Events in the Textbox for Blazor
slug: components/textbox/events
tags: telerik,blazor,textbox,events
published: true
position: 20
---

# Events

This article explsins the events available in the Telerik Textbox for Blazor:

* [OnChange](#onchange)
* [ValueChanged](#valuechanged)

## OnChange

The `OnChange` event fires when the new value is commited by the user either by pressing `Enter`, or when the input loses focus.

>caption Handle OnChange

````CSHTML
@result
<br />

<TelerikTextBox OnChange="@MyOnChangeHandler"></TelerikTextBox>

@code {
    string result;

    private void MyOnChangeHandler(object theUserInput)
    {
        // the handler receives an object that you may need to cast
        result = string.Format("The user entered: {0}", theUserInput);
    }
}
````

@[template](/_contentTemplates/common/general-info.md#event-callback-can-be-async)

>tip The `OnChange` event is a custom event and does not interfere with bindings, so you can use it together with models and forms.

>caption Handle OnChange and use two-way binding

````CSHTML
@result
<br />
model value: @theTbValue
<br />

<TelerikTextBox OnChange="@MyOnChangeHandler" @bind-Value="theTbValue"></TelerikTextBox>

@code {
    string result;

    string theTbValue { get; set; } = "lorem ipsum";

    private void MyOnChangeHandler(object theUserInput)
    {
        // the handler receives an object that you may need to cast
        result = string.Format("The user entered: {0}", theUserInput);
    }
}
````

## ValueChanged

The `ValueChanged` event fires upon every change (for example, keystroke) in the input.

>caption Handle ValueChanged

````CSHTML
@result
<br />

<TelerikTextBox ValueChanged="@( (string s) => MyValueChangeHandler(s) )"></TelerikTextBox>

@code {
    string result;

    private void MyValueChangeHandler(string theUserInput)
    {
        result = string.Format("The user entered: {0}", theUserInput);
    }
}
````

@[template](/_contentTemplates/common/general-info.md#event-callback-can-be-async)

@[template](/_contentTemplates/common/issues-and-warnings.md#valuechanged-lambda-required)

>caption Handle ValueChanged and provide initial value

````CSHTML
from the handler: @result
<br />
from model: @theTbValue
<br />

<TelerikTextBox ValueChanged="@( (string s) => MyValueChangeHandler(s) )" Value="@theTbValue"></TelerikTextBox>

@code {
    string result;

    public string theTbValue { get; set; } = "lorem ipsum";

    private void MyValueChangeHandler(string theUserInput)
    {
        result = string.Format("The user entered: {0}", theUserInput);

        //you have to update the model manually because handling the ValueChanged event does not let you use @bind-Value
        theTbValue = theUserInput;
    }
}
````

## See Also

* [ValueChanged and Validation]({%slug value-changed-validation-model%})
