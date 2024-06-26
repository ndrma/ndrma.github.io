# Personal Site / Blog

# Notes

## Hugo stuff

post

```
hugo new [future archetype here maybe] FOLDER/POSTNAME.md
```

Local server (with drafts showing)
```
hugo server -D
```

### Images

Images go into `content/CATEGORY/images/FILENAME.png`.

They are called in the blog with:
```
![Image title/text](/CATEGORY/images/FILENAME.png)
```

based on 
```
 use the following folder structure:

├── content
│ ├── archives.md
│ └── category
│ │ ├── blog-a
│ │ │ ├── index.md
│ │ │ ├── picture.jpg
│ │ ├── blog-b
│ │ │ ├── index.md
│ │ │ ├── picture.jpg

And then in for example in blog-a I use the following markdown to show the image:

![Alt text of image](/category/blog-a/picture.jpg "Image title")

Keep in mind the path can differ when using multiple languages and or other baseUrl's. But hopefully this helps a little.
```

## For cover images
Use this:
```
cover:
    image: images/FILENAME.png
    alt: "Cover Photo /article name"
    caption: ""
    relative: true
tags: ["houdini","vex","gis"]
categories: ["houdini", "snippets"]
```

### Attachments

Attachments, straight into post folder, then github link.

'new pull request on other branch'
