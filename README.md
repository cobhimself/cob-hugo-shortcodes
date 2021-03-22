# cob-hugo-shortcodes

This repository contains a couple of Hugo shortcode templates that make it easier to include
figures, examples, and references to other pages.

## Installation

This repository is a [hugo module](https://gohugo.io/categories/hugo-modules) and, as such, can be
added as a dependency in your hugo site.

If you haven't done so already, you should initialize the hugo module system:

```
hugo mod init github.com/<your_user>/<your_project>
```

Then, add this module's path in your config (config.yaml shown below):

```yaml
module:
  imports:
    path: "github.com/cobhimself/cob-hugo-shortcodes"
```

This will make this module a dependency of your hugo site and you will be able to use the shortcodes
without any further modification.

You can [update this module](https://gohugo.io/hugo-modules/use-modules/#update-modules) in your
project at any time.

## shortcodes

This hugo module provides the following shortcodes.

### ex

This shortcode makes it easy to include a file with code in it. The file's extension is used to
determine the highlighting.

| Parameter | Required | Description |
|-----------|----------|-------------|
| file      | Yes      | The location of the file to display (relative to the `content` folder)            |
| lang      | No       | The extension of the file is ignored and this value is used for the syntax highlighting |
| id        | No       | The id to be given to the figure node. Useful for creating in-page anchors |
| caption   | No       | The caption to use with the figure. |

#### Example

The example below would take the contents of the `ExampleClass.java` file and highlight it as Java
code.

```
{{< ex file="my/example/folder/ExampleClass.java" >}}
```

This would output the following HTML:

```html
<figure>
  <!-- the file's code highlighted as Java -->
</figure>
```

To include a caption and an id:

```
{{< ex
    file="my/example/folder/ExampleClass.java"
    caption="My example class"
    id="my-example-class-fig"
    lang="php"
>}}
```

This would output the following HTML and highlight it as if it were PHP:

```html
<figure id="my-example-class-fig">
  <!-- the file's code highlighted as PHP -->
  <figcaption>My example class</figcaption>
</figure>
```

### fig

This shortcode makes it easy to include the contents of a file and display it in a code block
without formatting. It is meant to be used with ascii drawing figures.

| Parameter | Required | Description |
|-----------|----------|-------------|
| file      | Yes      | The location of the file to display relative to the `content` folder            |
| id        | No       | The id to be given to the figure node. Useful for creating in-page anchors |
| caption   | No       | The caption to use with the figure. |

#### Example

The example below would take the contents of the `figure.txt` file and display it in a code block.

```text
{{< fig file="my/figure/folder/figure.txt" >}}
```

This would output the following HTML:

```html
<figure>
  <!-- the file's preformatted content -->
</figure>
```

To include a caption and an id:

```
{{< fig
    file="my/figure/folder/figure.txt"
    caption="My example figure"
    id="my-example-fig"
>}}
```

This would output the following HTML:

```html
<figure id="my-example-fig">
  <!-- the file's preformatted content -->
  <figcaption>My example figure</figcaption>
</figure>
```

### pageref

This shortcode makes it easy to create links to other pages. It accepts a page reference (like you
would give `relref`) as its single positional argument.

Any content provided inside the tag is used to override the text used for the generated link. By
default, the `.Title` of the page referenced will be used as the link's text. If the referenced
page has a `description` property, it will be used as the alternate text of the link.

#### Example

To add a reference to page "docs/api/blah" which has the `.Title` "Blah API" and a `.Description` of
"This page is so blah!":

```
{{% pageref "docs/api/blah" /%}}
```

> Notice the tag is self-closing!

This would output the following HTML:

```html
<a href="/docs/api/blah/" title="This page is so blah!">Blah API</a>
```

To override the `.Title` and use your own link text:

```
{{% pageref "docs/api/blah" %}}My own link text{{% /pageref %}}
```

This would output the following HTML:

```html
<a href="/docs/api/blah/" title="This page is so blah!">My own link text</a>
```