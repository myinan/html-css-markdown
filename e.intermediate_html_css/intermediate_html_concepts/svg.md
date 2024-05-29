# SVG (Scalable Vector Graphics)

### Introduction to SVG
Scalable Vector Graphics (SVG) is a widely used XML-based vector image format that is specifically designed for describing two-dimensional vector graphics. Unlike raster images (such as JPEG, PNG, and GIF), which are made up of pixels, SVG images are composed of geometric shapes, paths, and text elements defined using mathematical equations. This vector-based approach makes SVG images resolution-independent, allowing them to be scaled up or down without any loss of quality.

### Key Concepts of SVG

1. **Vectors and Paths:** SVG images are constructed using geometric shapes and paths. These shapes include lines, curves, circles, rectangles, and polygons. Paths are defined using commands that specify how to move and draw lines between points, creating intricate shapes.

2. **Coordinates and Units:** SVG uses a coordinate system to position and size elements. The coordinate system places the origin (0,0) at the top-left corner of the image. Units can be specified in various ways, including pixels (px), percentages (%), ems (relative to the font size), and more.

3. **Styling:** SVG images can be styled using CSS (Cascading Style Sheets) attributes. This includes setting colors, stroke widths, opacity, gradients, patterns, and more. This separation of style from content allows for easy customization.

4. **Text Elements:** SVG supports text elements, allowing you to add labels, titles, and descriptions to your graphics. Text can be styled like other elements and can be positioned and manipulated using attributes.

5. **Gradients and Patterns:** SVG supports both linear and radial gradients, which enable smooth color transitions. Patterns can be defined and applied to elements, allowing for repeating images as fills.

6. **Transformations:** SVG allows you to apply transformations to elements, such as scaling, rotation, translation, and skewing. These transformations can be combined to create complex effects.

7. **Interactivity:** SVG images can have interactive elements such as links and tooltips, and they can respond to events like clicks, mouseovers, and more. This makes SVG suitable for creating interactive infographics, maps, and user interfaces.

### SVG vs. Raster Formats

#### SVG (Vector):
- **Scalability:** SVG images are resolution-independent, meaning they can be scaled up or down without any loss of quality.
- **Small File Sizes:** SVG files are typically smaller in size compared to raster formats, especially for complex graphics.
- **Editing:** SVG images can be edited using text editors or specialized vector graphics software.
- **Text Clarity:** Text in SVG remains sharp at any size, making it suitable for logos, typography, and illustrations.
- **Animations and Interactivity:** SVG supports animations and interactivity through CSS or JavaScript.

#### Raster Formats (e.g., JPEG, PNG, GIF):
- **Pixel-based:** Raster images are composed of individual pixels, limiting their scalability.
- **Large File Sizes:** Raster images can become large in size, especially at high resolutions.
- **Editing Limitations:** Raster images can lose quality when edited, and certain changes are more challenging (e.g., scaling up).
- **Text Quality:** Text in raster images can become blurry or pixelated when scaled up.
- **Limited Interactivity:** Raster images can have some interactivity (e.g., clickable areas), but not to the same extent as SVG.

In summary, SVG is a versatile format for creating scalable and interactive vector graphics. It's suitable for a wide range of applications, including web graphics, logos, icons, data visualizations, and more. While raster formats have their advantages, SVG's flexibility, scalability, and text clarity make it a powerful choice for many design scenarios.

### Vector Graphics vs Raster Graphics
Vector graphics refer to a type of digital image format that is created using mathematical equations to define various elements, such as lines, curves, shapes, and colors. These elements are represented as mathematical objects like points, lines, and curves, rather than a grid of individual pixels like in raster or bitmap graphics.

The key characteristic of vector graphics is that they are resolution-independent, meaning they can be scaled up or down without any loss of image quality. This is in contrast to raster graphics, where enlarging an image can lead to a loss of clarity and sharpness as the individual pixels become more visible.

Vector graphics are commonly used for creating logos, illustrations, diagrams, typography, and other graphics where precise shapes and scalable output are important. They are often created using software like Adobe Illustrator, CorelDRAW, Inkscape, or other vector-based design tools.

Some advantages of vector graphics include:

1. **Scalability:** Vector graphics can be resized without losing quality, making them suitable for various applications.

2. **Small File Sizes:** Vector files are typically smaller in size compared to their raster counterparts because they only need to store mathematical instructions for rendering the image, rather than individual pixel data.

3. **Smooth Edges:** Vector graphics produce smooth lines and curves regardless of the size or resolution.

4. **Editing Flexibility:** It's easier to edit and manipulate individual elements within a vector graphic. You can modify shapes, colors, and other attributes without compromising quality.

However, vector graphics are not suitable for all types of images. They are best suited for images with well-defined shapes and limited gradients or complex textures. When dealing with photographs or images requiring intricate shading, raster graphics (pixel-based images) are generally more appropriate.

![Vector vs Raster Graphics](../../../img/vector-vs-raster.jpg "Vector vs Raster Graphics")

### XML
XML stands for "eXtensible Markup Language." It is a markup language that is designed to store and transport structured data in a human-readable format. XML is not a programming language; rather, it is a way to structure data using a set of rules for defining and describing elements and their relationships.

In XML, data is enclosed within tags, which are defined by angle brackets ("<" and ">"). These tags create a hierarchical structure that represents the relationships between different pieces of data. Each tag can have attributes (name-value pairs) that provide additional information about the data.

XML is widely used for various purposes, including:

1. **Data Interchange:** XML is used to exchange data between different systems and applications, regardless of the platforms or programming languages they use. This makes it particularly useful for communication between heterogeneous systems.

2. **Configuration Files:** Many software applications use XML to store configuration settings in a structured and readable manner.

3. **Web Services:** XML is commonly used for structuring data in web services, where different applications can communicate and exchange information over the internet.

4. **Document Formats:** XML is used as the foundation for various document formats, such as XHTML (for web content), SVG (for scalable vector graphics), and more.

5. **Data Storage:** XML can also be used as a format for storing structured data in databases or files.

It's worth noting that while XML has been widely used, other formats like JSON (JavaScript Object Notation) have gained popularity due to their simplicity and ease of use, particularly for web-related applications. JSON is more lightweight and more closely aligned with how data is represented in programming languages like JavaScript, which makes it easier for developers to work with in modern web applications.

### XML and SVG
XML (eXtensible Markup Language) and SVG (Scalable Vector Graphics) are related in the sense that SVG is a specific XML-based format used for describing two-dimensional vector graphics. SVG is essentially a markup language that conforms to XML rules and is used to define graphics, such as shapes, lines, curves, and text, in a way that is scalable and resolution-independent.

Here's how XML and SVG are related:

1. **XML Structure:** SVG documents are written using XML syntax. This means that an SVG file is essentially an XML document that follows the rules and conventions of XML. SVG tags, attributes, and content are defined using XML format, making it easy to manipulate and process SVG graphics using XML parsers and tools.

2. **Hierarchical Format:** Just like XML, SVG uses a hierarchical structure where different elements are nested within each other. Each SVG element is represented by an XML tag, and its attributes provide information about the properties of that element.

3. **Scalable Graphics:** SVG's main purpose is to describe graphics in a way that remains sharp and clear regardless of the size at which it is displayed. This is because SVG defines graphics using mathematical equations and coordinates, rather than pixels. When you resize an SVG image, the mathematical descriptions are recalculated, maintaining the image's quality.

4. **Web and Display:** SVG is widely used for creating graphics on the web. It can be embedded directly into HTML documents and displayed by modern web browsers. This makes it a popular choice for creating interactive and responsive graphics, such as icons, diagrams, and even entire illustrations.

5. **Vector Graphics:** SVG focuses on vector graphics, which are graphics defined by mathematical equations and geometric shapes, rather than pixel-based raster graphics. This makes SVG graphics suitable for scenarios where high-quality graphics are required, such as logos, icons, and illustrations.

In summary, SVG is a specialized use case of XML where the XML structure is used to define scalable vector graphics. The relationship between XML and SVG lies in the fact that SVG documents adhere to the XML standard and benefit from its hierarchical, structured, and human-readable nature.

### Creating SVGs
Creating SVGs (Scalable Vector Graphics) involves creating or editing vector graphics using software tools that support SVG format. Here are a few methods you can use to create SVGs:

1. **Graphic Design Software**:
   - **Adobe Illustrator**: Illustrator is a professional vector graphics software that allows you to create intricate SVGs with precision. It offers a wide range of tools for drawing, editing, and manipulating vector shapes.
   - **Inkscape**: Inkscape is a free and open-source vector graphics editor. It's a powerful tool for creating SVGs and is a great choice for those who don't have access to Adobe Illustrator.
   - **CorelDRAW**: CorelDRAW is another commercial vector graphics software that can be used to create SVGs.

2. **Online SVG Editors**:
   - **SVG-Edit**: SVG-Edit is a free, web-based SVG editor that you can use directly in your browser. It's a simple tool for creating basic SVG graphics.
   - **Vectr**: Vectr is an online vector graphics editor that supports SVG export. It's user-friendly and suitable for beginners.

3. **Code Editors**:
   - If you're comfortable with writing SVG code, you can create SVGs using a simple text editor. SVG is XML-based, so you can hand-write SVG markup. This method is best suited for simple shapes or modifications to existing SVGs.

4. **Conversion Tools**:
   - If you have existing graphics in other formats (e.g., PNG, JPEG), you can use online conversion tools to convert them to SVG. Keep in mind that these conversions may not always result in perfect vector graphics, especially for complex images.

Here's a basic example of SVG markup for a simple rectangle:

```xml
<svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
  <rect x="10" y="10" width="80" height="80" fill="blue" />
</svg>
```

This SVG code creates a blue rectangle with a width and height of 80 units, positioned at coordinates (10, 10).

Once you have created your SVG, you can incorporate it into your HTML documents. Of course, you can also incorporate an already existing SVG into your HTML instead of creating it from the ground up.

### Adding SVG to HTML document
There are primarily two ways to add SVG to an HTML document:

1. **Inline SVG**: This method involves directly embedding the SVG code within your HTML document using the `<svg>` element. Inline SVG allows you to define your SVG directly in your HTML code, making it easy to manipulate using CSS and JavaScript.

    ```html
    <svg width="100" height="100">
      <circle cx="50" cy="50" r="40" stroke="black" stroke-width="2" fill="red" />
    </svg>
    ```

    Directly adding SVG code into HTML unlocks the full potential of SVGs, making it possible to style or even animate SVGs with CSS.

2. **External SVG File**: You can also create an SVG file (with a `.svg` extension) and include it in your HTML using the `<img>` element or the `<object>` element.

    Using the `<img>` element:
    ```html
    <img src="path/to/your.svg" alt="SVG Image">
    ```

    Using the `<object>` element:
    ```html
    <object data="path/to/your.svg" type="image/svg+xml"></object>
    ```

    The `<object>` element is more versatile as it allows for better integration of CSS and JavaScript with the SVG content than the `<img>` element.

### Anatomy of an SVG

```html
<div class="container">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
        <rect x="0" y="0" width="100" height="100" fill="burlywood"/>
        <path d="M 10 10 H 90 V 90 L 10 60" fill="transparent" stroke="black" stroke-width="3"/>
        <circle cx="50" cy="50" r="20" class="svg-circle"/>
        <g class="svg-text-group">
            <text x="20" y="25" rotate="10" id="hello-text">Hello!</text>
            <use href="#hello-text" x="-10" y="65" fill="white"/>
        </g>
    </svg>
</div>
```

1. `<svg>`: The root element of an SVG document. It defines the beginning of an SVG graphic. The `xmlns` attribute specifies the XML namespace for SVG.

The `xmlns` attribute is used in the root element of an SVG document to declare the default namespace for the document. In other words, it defines the XML namespace that all the elements and attributes within the SVG document belong to. The value of the `xmlns` attribute is the URI that uniquely identifies the SVG namespace. The `xmlns` attribute plays a vital role in ensuring proper interpretation and rendering of SVG graphics by indicating which set of rules and definitions should be applied to the SVG elements and attributes within the document. 

Note that namespace names are just strings, so the fact that the SVG namespace name also looks like a URI isn't important. URIs are commonly used because they are unique, but the intention is not to "link" somewhere. (In fact, URIs are used so frequently that the term "namespace URI" is commonly used instead of "namespace name".)

2. `viewBox="0 0 100 100"`: The `viewBox` attribute defines the coordinate system and aspect ratio of the SVG canvas. In this case, it sets the coordinate system to range from (0, 0) to (100, 100).

3. `<rect>`: A rectangular shape. It's defined by its position (`x` and `y`), width, height, and fill color (`fill`). In this case, it creates a burlywood-colored rectangle that covers the entire canvas.

4. `<path>`: A path element that defines a custom shape using path data (`d`). The path data consists of commands such as `M` (move to), `H` (horizontal line), `V` (vertical line), and `L` (line to). It outlines a shape that resembles a triangle. The `fill` attribute is set to transparent, and the `stroke` attribute defines the outline color. `stroke-width` specifies the width of the stroke.

5. `<circle>`: Draws a circle with a center at coordinates (`cx`, `cy`) and a radius (`r`). The `class` attribute assigns the class name "svg-circle" to the circle, which can be used for styling and targeting with CSS.

6. `<g>`: A group element that groups multiple SVG elements together. It's used to apply transformations or styles to a group of elements. The `<g>` element doesn't have any meaning as itself and it's used in XML in the same manner of `<div>` or `<span>` in HTML.

7. `<text>`: Renders text at the specified coordinates (`x`, `y`). In this case, it writes "Hello!" at (20, 25). The `rotate` attribute rotates the text element, and `id` specifies an identifier for the text.

8. `<use>`: Reuses an existing SVG element by referencing its `id` using the `href` attribute. In this case, it reuses the "hello-text" text element at a new position (x: -10, y: 65) and fills it with white.

---
### Knowledge Check

**Q1.** What is the xmlns attribute?

**A1.** The `xmlns` attribute is used to declare the default namespace for the SVG document. In other words, it defines the XML namespace that all the elements and attributes within the SVG document belong to. The value of the `xmlns` attribute is the URI that uniquely identifies the SVG namespace. The `xmlns` attribute plays a vital role in ensuring proper interpretation and rendering of SVG graphics by indicating which set of rules and definitions should be applied to the SVG elements and attributes within the document. 

**Q2.** What are some situations where you wouldn’t want to use SVG?

**A2.** SVGs are generally not suitable for displaying images with complex graphics, shading etc. For displaying complex images, raster formats(jpg,png etc.) should be used.

**Q3.** What are the benefits of “inlining” your SVGs? What are the drawbacks?

**A3.** Inlining SVG into HTML makes manipulating, styling and animating said SVG element with CSS possible. On the other hand, inlining might cause the code to become less readable or if the SVG is large, it might delay loading rest of the HTML.