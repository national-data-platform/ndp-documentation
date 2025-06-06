# Data Catalog 

One of the key features of NDP is its extensive and diverse data catalog, which offers a broad selection of datasets and data streams covering various scientific domains. This catalog is enriched through collaboration with numerous organizations and researchers, who contribute datasets which are accessible via the platform’s registration service. 

To streamline data discovery, NDP integrates a search engine that enables users to locate datasets quickly and efficiently. 

- **Substring Search**: This search method returns a list of datasets containing the specified substring in either the dataset name or metadata. This allows for broad searches across the dataset collection, making it easy to locate relevant data with basic keywords.
- **Conceptual Search**: This search method returns datasets that match specific annotations, along with detailed statistics related to the occurrences of the search term within the available Open Knowledge Networks (OKNs). OKNs are semantic databases that provide linkages between datasets, concepts, and entities, facilitating more context-aware data exploration and discovery. Additionally, the search results include detailed statistics, such as frequency of occurrence, co-occurrence with other concepts, and related entities.
- **Filtered Search**: Users have the option to filter their search results by the contributing organization. This feature is particularly useful for those looking to access datasets from specific institutions, research groups, or initiatives. 

## Advanced Search

The advanced search feature allows you to perform targeted searches across various metadata fields in the data catalog. You can use the search text box to search for specific keywords, phrases, or values across multiple fields.

#### Searchable Fields

The following fields are searchable:

- `all_text`: Searches across all metadata fields
- `name`: Searches the dataset's name
- `notes`: Searches the dataset's notes
- `description`: Searches the dataset's description
- `organization_name`: Searches the name of the organization that owns or is responsible for the dataset
- `title`: Searches the dataset's title

#### Search Syntax

The syntax to construct your search queries is the following:

- Use a colon (:) to specify the field you want to search, followed by the search term. For example: `notes:Lidar`
- Use the `AND` operator to combine multiple search terms across different fields. For example: `notes:Lidar AND description:creek`.You can also use other logical operators, such as `OR` and `NOT`, to refine your search queries.

You can learn more about the search syntax in the [Lucene documentation](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html)

## Spatial Temporal Search / Map Search

Soon
