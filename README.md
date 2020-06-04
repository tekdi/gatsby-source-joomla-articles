# gatsby-source-joomla-articles
Source plugin for pulling data into [Gatsby](https://github.com/gatsbyjs) from
Joomla(Articles)  sites using the Rest API.
## Articles and custom Fields
This module currently pulls the following entities from Joomla(Articles):
- [x] All entities are supported by Jommla articles(Tags,Custom fields)
## Install
npm install <git repo url>
## How to use
you need to add the plugin information in the configuration of the gatsby site.(gatsby-config.js)
  ```javascript
// In your gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: `gatsby-source-joomla-articles`,
      options: {
        //URL of the Joomla project (Rest api to fetch the articles)
        baseUrl: "url",
      rowLimits:{
        //Limit:How many articles you want to fetch.
        limit:20,
        step:100,
        //Step : How many articles you want to fetch at one fetch request.
        },
      },
    }
  ],
}
```
## How to query
  ### Query for all articles
  
```graphql
query allArticleQuery {
  allJoomlaArticle {
    edges {
      node {
        id
        title
        state
        fulltext
        access
        alias
        introtext
        language
        images {
          float_fulltext
          float_intro
          image_fulltext
          image_fulltext_alt
          image_fulltext_caption
          image_intro
        }
        tags {
          itemTags {
            title
            access
            alias
            checked_out
            checked_out_time
            created_by_alias
            version
          }
        }
        custom_fields {
          field_name {
            access
            checked_out
            checked_out_time
            context
            created_user_id
            default_value
            description
            group_id
            label
            language
            name
            note
            required
            title
          }
        }
      }
    }
  }
}
```
  ### Query for single article
  
```graphql
query ArticleQuery {
    joomlaArticle {
      title
      access
      alias
      featured
      fulltext
      hits
      id
      publish_up
      state
      catid {
        catid
        title
      }
      images {
        float_fulltext
        float_intro
        image_fulltext
        image_fulltext_alt
        image_fulltext_caption
        image_intro
      }
      internal {
        content
        description
        fieldOwners
      }
      introtext
      language
      modified
      publish_down
      parent {
        id
      }
      tags {
        itemTags {
          title
          access
          alias
          checked_out
          checked_out_time
          created_by_alias
          version
        }
      }
     
    }
  }
}
```

  
