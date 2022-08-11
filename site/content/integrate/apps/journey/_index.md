---
title: Journey Example
description: An example of an Apps journey
weight: 1
---

This is the starting page of the journey; effectively "step 1".<br/>

Some introductory text will go here. It will explain the goal of the journey as a whole and note that there are several steps.

## Step 1: Quick Start

The goal of this step will be explained here. For example: "After completing this step, you will have a fully-functional App integration that does xxxxx."

{{<note>}}
This note will inform the reader that they need to set up their dev environment and start a new project in their IDE.
{{</note>}}
<br/>

1. Define a manifest

    Briefly describe what a manifest is and what it means to an App.
    
    Create the manifest object and fill it in.
    
    ```go
    var manifest = apps.Manifest{
      AppID:   apps.AppID("hello-world"),
      Version: apps.AppVersion("0.1.0"),
      // ...
    }
    ```

2. Define bindings

    Briefly describe what a binding is and what it means to an App.
    
    Create the bindings object and fill it in.
    
    ```go
   // NOTE: this example is incorrect and will change.
    var bindings = []apps.Binding{
      {
        Location: apps.LocationChannelHeader,
        Bindings: []apps.Binding{
          {
            Location: "send-button",
            Icon:     "icon.png",
            Label:    "send hello message",
            Submit: &apps.Call{
              Path: "/send-modal",
            },
          },
        },
      },
      // ...
    }
    ```

3. Define REST endpoints

    Briefly describe what the endpoints, in this case `/manifest.json` and `/bindings`, mean to an App.

    Create a new router and add some endpoints.

    ```go
    func main() {
      mux := http.NewServeMux()
      mux.HandleFunc("/manifest.json", httputils.DoHandleJSON(appManifest))
      mux.HandleFunc("/bindings", httputils.DoHandleJSON(appBindings))
      server := http.Server{
        Addr:    ":4000",
        Handler: mux,
      }
      _ = server.ListenAndServe()
    }
    ```
   
4. Start the App

    Inform the reader that they will start an instance of their App.

    ```shell
    go run .
    ```
   
5. Install the App in Mattermost

    Inform the reader that they need to run the following in a channel:

    ```
    /apps install http http://localhost:4000/manifest.json
    ```
   
6. Test the App

    Walk the reader through using the App.


### That's it! You've got a working Mattermost App!

Summarize what the reader learned.

Here's a link to download the App you built: &lt;link goes here&gt;

Are you ready for the next step? [Step 2: Forms]({{< ref "integrate/apps/journey/step2" >}})
