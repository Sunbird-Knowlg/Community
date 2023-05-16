# Content import and preview folder creation

## Offline play

The v1 player is capable to play the content offline locally. Here are the steps to load the content locally:

* Download and extract the ECAR file in a local folder.
*   Replace the existing ECAR of the content

    ```
    Got to  => sunbird-content-player/player/public/fixture-stories/custom_eval
    Replace => assets, index.json and widgets folder with extracted files
    ```
* Refresh the page in the local environment.

## Create a preview folder

The v1 player is capable to provide the build to verify the changes locally. Here are the steps to generate the preview folder locally:

* Go to _sunbird-content-player/player_
*   Run the following command :-&#x20;

    <pre><code><strong>> npm run build-preview
    </strong></code></pre>
*   ’The preview folder will create at the following path

    ```
    sunbird-content-player/player/www
    ```
* Just copy and paste it into your project and follow the given [instructions](https://github.com/project-sunbird/sunbird-content-player/tree/release-5.1.0#how-to-render-the-contents)

