# Travis Exitwp

This is a "cloud" version of [Exitwp](https://github.com/thomasf/exitwp). It is provided to those who do not know how to run Python scripts (or do not bother to run the script locally). Basically you upload a WordPress XML file and you will get a download link to a zip file of your posts/pages in Markdown.

1. Export your WordPress posts to XML (from your WordPress Admin panel: `Tools -> Export`).

1. Fork this repository, upload the `.xml` file, and follow Github's guide to submit a pull request.

    ![fork](https://user-images.githubusercontent.com/163582/27658948-6922360a-5c17-11e7-8a8e-727cf3774bab.png)
    
    ![commit](https://user-images.githubusercontent.com/163582/27658950-692b3f5c-5c17-11e7-8880-79d6dc622fd7.png)

1. Wait for a minute or so, and you should see a green checkmark on your commit. Click it to see the detailed log on Travis CI.

    ![PR](https://user-images.githubusercontent.com/163582/27658949-69246f7e-5c17-11e7-9c37-f3207d3ba168.png)

    If the build was successful, you should see the last few lines of the log like this:

    ```bash
    zip -r build build
      adding: build/ (stored 0%)
      adding: build/jekyll/ (stored 0%)
      adding: build/jekyll/example.com/ (stored 0%)
      adding: build/jekyll/example.com/about/ (stored 0%)
      adding: build/jekyll/example.com/about/index.markdown (deflated 36%)
      adding: build/jekyll/example.com/_posts/ (stored 0%)
      adding: build/jekyll/example.com/_posts/2007-07-13-a-sample-post.markdown (deflated 27%)
    curl -F "file=@build.zip" https://file.io
    {"success":true,"key":"4z2Ajm","link":"https://file.io/4z2Ajm","expiry":"14 days"}
    
    The command "../build.sh" exited with 0.
    ```
    
    Open the `https://file.io/xxxxxx` link to download the zip archive. It contains the Markdown files converted from your WordPress posts. **Note** you only have one chance to download it (once downloaded, it will be deleted permanently). Read the **blogdown** book to know how to proceed to Hugo: https://bookdown.org/yihui/blogdown/from-jekyll.html.

Many thanks to [@thomasf](https://github.com/thomasf) for providing the Exitwp scripts. All I did was to configure Travis (`.travis.yml`) and provide the documentation here. I'd like to thank file.io, too. File uploading via a one-liner command. That is very cool.
