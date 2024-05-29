# Tables
In HTML, tables are a fundamental structure used to display and organize data in a tabular format. Tables are made up of rows and columns, with each cell in the table containing data or other HTML elements like text, images, links, or even nested tables. Tables are a powerful tool for presenting information in a structured and visually appealing manner. To create tables in HTML, you use a combination of HTML elements, primarily the `<table>`, `<tr>`, `<th>`, and `<td>` elements.

Let's break down the key elements and attributes associated with creating tables in HTML:

### 1. `<table>` Element:
   - The `<table>` element is the container for the entire table structure.
   - It has various attributes to control the table's appearance and behavior, such as `border`, `width`, `cellpadding`, `cellspacing`, and more.

   Example:
   ```html
   <table border="1" cellpadding="5" cellspacing="0">
      <!-- Table content goes here -->
   </table>
   ```

### 2. `<tr>` Element (Table Row):
   - The `<tr>` element defines a row in the table.
   - It contains one or more `<th>` (table header cell) or `<td>` (table data cell) elements as its children.
   - Table rows ensure that data aligns correctly in rows across the table.

   Example:
   ```html
   <tr>
      <th>Header 1</th>
      <th>Header 2</th>
   </tr>
   ```

### 3. `<th>` Element (Table Header Cell):
   - The `<th>` element is used to define header cells within the table.
   - Header cells typically contain labels for columns or groups of columns.
   - They are usually bold and centered by default.

   Example:
   ```html
   <tr>
      <th>Employee ID</th>
      <th>Name</th>
      <th>Department</th>
   </tr>
   ```

### 4. `<td>` Element (Table Data Cell):
   - The `<td>` element is used for regular data cells within the table.
   - These cells contain the actual data that you want to display.

   Example:
   ```html
   <tr>
      <td>001</td>
      <td>John Doe</td>
      <td>Marketing</td>
   </tr>
   ```

### 5. Column and Row Span:
   - You can use the `colspan` attribute with `<th>` and `<td>` elements to make a cell span multiple columns.
   - Similarly, you can use the `rowspan` attribute to make a cell span multiple rows.

   Example:
   ```html
   <tr>
      <th colspan="2">Employee Details</th>
      <th>Salary</th>
   </tr>
   ```

### 6. Styling and Formatting:
   - You can use CSS to style and format tables, including setting background colors, borders, text alignment, and more.
   - CSS classes and IDs can be added to table elements to target them for styling.

### 7. Caption:
   - The `<caption>` element is used to provide a title or caption for the entire table.
   - It is typically placed immediately after the opening `<table>` tag.

   Example:
   ```html
   <table>
      <caption>Employee Information</caption>
      <!-- Table content goes here -->
   </table>
   ```

### 8. Accessibility:
   - It's important to use semantic HTML and include proper table headers (`<th>`) with associated data cells (`<td>`) to ensure accessibility for screen readers and other assistive technologies.

## Styling spesific columns with \<col>
`<col>` elements are specified inside a `<colgroup>` container just below the opening `<table>` tag.

```html
<table>
  <colgroup>
    <col />
    <col style="background-color: yellow" />
  </colgroup>
  <tr>
    <th>Data 1</th>
    <th>Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td>Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td>Jazz</td>
  </tr>
</table>
```

Effectively we are defining two "style columns", one specifying styling information for each column. We are not styling the first column, but we still have to include a blank `<col>`` element — if we didn't, the styling would just be applied to the first column.

If we wanted to apply the styling information to both columns, we could just include one `<col>` element with a span attribute on it, like this:

```html
<colgroup>
  <col style="background-color: yellow" span="2" />
</colgroup>
```

Just like colspan and rowspan, span takes a unitless number value that specifies the number of columns you want the styling to apply to.

## Adding structure with \<thead>, \<tfoot>, and \<tbody>
As your tables get a bit more complex in structure, it is useful to give them more structural definition. One clear way to do this is by using `<thead>`, `<tfoot>`, and `<tbody>`, which allow you to mark up a header, footer, and body section for the table.

These elements don't make the table any more accessible to screen reader users, and don't result in any visual enhancement on their own. They are however very useful for styling and layout — acting as useful hooks for adding CSS to your table.

## The `scope` attribute
The `scope` attribute in HTML is used in conjunction with the `<th>` (table header cell) element to specify the scope or context of a header cell in an HTML table. It helps screen readers and other assistive technologies understand the relationship between the header cells and the data cells within a table, making tables more accessible for users with disabilities.

The `scope` attribute can take one of four values:

1. `scope="row"`: This is used to indicate that the header cell applies to an entire row of data cells. It means that the header cell provides information about the data in the row.

2. `scope="col"`: This is used to indicate that the header cell applies to an entire column of data cells. It means that the header cell provides information about the data in the column.

3. `scope="rowgroup"`: This is used to indicate that the header cell applies to a group of rows.

4. `scope="colgroup"`: This is used to indicate that the header cell applies to a group of columns.

Using the `scope` attribute appropriately enhances the accessibility of tables, making it clear which header cells correspond to which data cells and helping screen readers provide more meaningful information to users with disabilities.

---
### Knowledge Check

**Q1.** What is a table?

**A1.** A table is a structure to present data in rows and columns.

**Q2.** Why is it a bad idea to use HTML Tables for page layout?

**A2.** HTML tables are not designed for page layout but to present data in a structured manner. Using tables for page layout hinders accessibility of the webpage, screenreaders can't parse the page correctly if it's laid out using an HTML table.

**Q3.** What are caption elements useful for?

**A3.** Caption element provides a brief summary of what table is about, also useful for accessibility reasons.

**Q4.** What is the scope attribute?

**A4.** With the scope attribute, we can define the "scope" of a `<th>` element thus provide more accesibility for blind users. When we define a scope for a particular `<th>` element, screenreaders will first read the associated data with that header thus provide a more accessible web experience to users with disabilities.
