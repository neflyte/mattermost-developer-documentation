---
title: "Step 2: Forms"
description: Use forms with a Mattermost App
weight: 10
---

The goal of this step will be explained here. For example: "After completing this step, you will have an App integration that does xxxxx."

This text will introduce the concept of forms and what they can do.
After each part of this page, the reader should be able to run their App to see their changes.

1. Display an informational form

    Create a basic form that has some text and is triggered by the same mechanism as used in Step 1.

    ```go
    var appForm = apps.Form{
      // ...
    }
    ```

    Update bindings to display the form.

    ```go
    var appBindings = []apps.Binding{
      // ...
      {
        // new binding here
      },
      // ...
    }
    ```

    Add new REST endpoints for the form.

    ```go
    func send(w http.ResponseWriter, r *http.Request) {
      // ...
    }
   
    func main() {
      // ...
      mux.HandleFunc("/send/form", httputils.DoHandleJSON(appForm))
      mux.HandleFunc("/send/submit", send)
      mux.HandleFunc("/send-modal/submit", httputils.DoHandleJSON(appForm))
      // ...
    }
    ```

    Test the changes.

2. Accept input on the form

    Update the form to have an input of any data type.

    ```go
    var appForm = apps.Form{
      // ...
    }
    ```

    Update the `send` function to include the form data with the message that gets posted

    ```go
    func send(w http.ResponseWriter, r *http.Request) {
      // ...
    }
    ```
   
    Test the changes.

    For more examples of each kind of form field, click here: &lt;link to per-field examples&gt;

3. Dynamic forms

    This text will describe what we mean by "dynamic forms" and introduce what we are going to add to the existing form.

    - Update the form.
    - Update the bindings.
    - Add/update REST endpoints.
    
    Test the changes.

### Summary

Summarize what the reader learned.

Here's a link to download the App up to this point: &lt;link goes here&gt;

Are you ready for the next step? [Step 3: Bindings]({{< ref "integrate/apps/journey/step3" >}})
