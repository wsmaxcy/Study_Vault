# Google Fu

## Overview
Google Fu refers to the skill of using advanced search operators and techniques to find information on the internet using Google. It is an essential skill for OSINT (Open Source Intelligence) gathering, research, and finding specific data effectively.

## Features
- **Advanced search operators:** Use various operators to narrow down search results.
- **Effective data retrieval:** Find precise information quickly.
- **OSINT gathering:** Collect open-source intelligence from publicly available data.

## Website
- [Google Search](https://www.google.com/)

## Basic Usage
Google Fu involves using specific search operators and techniques to refine your search queries and get better results.

### Common Search Operators

#### Exact Match
Use quotes to search for an exact phrase:
```sh
"search term"
```

#### Exclude Terms
Use the minus sign to exclude terms from the results:
```sh
search term -exclude
```

#### Site-Specific Search
Search within a specific website:
```sh
site:example.com search term
```

#### File Type
Search for specific file types:
```sh
filetype:pdf search term
```

#### OR Operator
Search for either one term or another:
```sh
term1 OR term2
```

#### Intitle
Search for pages with a specific word in the title:
```sh
intitle:"search term"
```

#### Inurl
Search for pages with a specific word in the URL:
```sh
inurl:searchterm
```

#### Cache
View the cached version of a webpage:
```sh
cache:example.com
```

### Advanced Techniques

#### Combine Operators
Combine multiple operators to refine your search:
```sh
site:example.com "search term" -exclude filetype:pdf
```

#### Use Wildcards
Use the asterisk (*) as a wildcard to replace a word:
```sh
"best * in 2023"
```

#### Related Sites
Find sites related to a particular domain:
```sh
related:example.com
```

### Practical Examples

#### Finding Specific File Types
To find PDF files about cybersecurity:
```sh
filetype:pdf cybersecurity
```

#### Excluding Unwanted Results
To find information about Python programming but exclude results about snakes:
```sh
Python programming -snakes
```

#### Researching on a Specific Site
To find articles about AI on the New York Times website:
```sh
site:nytimes.com AI
```

#### Searching for Cached Pages
To view a cached version of a recently updated page:
```sh
cache:example.com
```

## Best Practices
- **Use quotes for exact phrases:** Enclose exact phrases in quotes to find precise matches.
- **Exclude irrelevant results:** Use the minus operator to exclude unwanted terms from your results.
- **Specify sites and file types:** Narrow down your search by specifying websites and file types.
- **Experiment with operators:** Combine different search operators to achieve the best results.

## References
- [Google Search Operators](https://support.google.com/websearch/answer/2466433?hl=en)
- [Google Advanced Search](https://www.google.com/advanced_search)
