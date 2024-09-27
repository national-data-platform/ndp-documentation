# Advanced Search

The advanced search feature allows you to perform targeted searches across various metadata fields in the data catalog. You can use the search text box to search for specific keywords, phrases, or values across multiple fields.

### Searchable Fields

The following fields are searchable:

- `all_text`: Searches across all metadata fields
- `name`: Searches the dataset's name
- `notes`: Searches the dataset's notes
- `description`: Searches the dataset's description
- `organization_name`: Searches the name of the organization that owns or is responsible for the dataset
- `title`: Searches the dataset's title

### Search Syntax

The syntax to construct your search queries is the following:

- Use a colon (:) to specify the field you want to search, followed by the search term. For example: `notes:Lidar`
- Use the `AND` operator to combine multiple search terms across different fields. For example: `notes:Lidar AND description:creek`.You can also use other logical operators, such as `OR` and `NOT`, to refine your search queries.

You can learn more about the search syntax in the [Lucene documentation](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)

### Temporal Search

In addition to searching metadata fields, *Advanced Search* also allows searching for datasets based on their temporal coverage. Use the Start and End date fields to specify a time range, and the search engine will return datasets that fall within that range. This is useful for finding datasets that cover a specific period of time or event.

### Spatial Search

The advanced search feature also includes a map view that allows you to search for datasets based on their spatial coverage. You can draw a polygon on the map to define a spatial extent, and the search engine will return datasets that intersect with that polygon. This is useful for finding datasets that cover a specific geographic area or region.