This repository contains a couple of Hugo shortcode templates that make it easier to include
figures, examples, and references to other pages.

# ex

This shortcode makes it easy to include a file with code in it. The file's extension is used to
determine the highlighting.

| Parameter | Required | Description |
|-----------|----------|-------------|
| file      | Yes      | The location of the file to display relative to the `content` folder            |
| lang      | No       | The extension of the file is ignored and this value is used for the syntax highlighting |
| id        | No       | The id to be given to the figure node. Useful for creating in-page anchors |
| caption   | No       | The caption to use with the figure. |

## Example

The example below would take the contents of the `ExampleClass.java` file and highlight it as Java
code.

```text
{{< ex file="my/example/folder/ExampleClass.java" >}}
```

# fig

This shortcode makes it easy to include the contents of a file and display it in a code block
without formatting. It is meant to be used with ascii drawing figures.

| Parameter | Required | Description |
|-----------|----------|-------------|
| file      | Yes      | The location of the file to display relative to the `content` folder            |
| id        | No       | The id to be given to the figure node. Useful for creating in-page anchors |
| caption   | No       | The caption to use with the figure. |

## Example

The example below would take the contents of the `figure.txt` file and display it in a code block.

```text
{{< fig file="my/figure/folder/figure.txt" >}}
```

# pageref

This shortcode makes it easy to create links to other pages. All parameters are positional.

| Argument Position | Required | Description |
|-------------------|----------|-------------|
| 1                 | Yes      | The location of the file to display relative to the `content` folder            |
| 2                 | No       | The id to be given to the figure node. Useful for creating in-page anchors |
