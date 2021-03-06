# awesometalks.party data dump

this is a full data backup of https://github.com/SaraVieira/awesome-talks, because she wants to [wind down the graphcms database](https://github.com/SaraVieira/awesome-talks/issues/119).

I extracted the data simply by querying the graphiql endpoint: https://api-eu-central-1.graphcms.com/v2/ck67w2glj2d7p01936oo7gna0/master?query=%7Bvideoses%20%7B%0A%20%20id%0A%7D%7D 

since its graphql there is no one right way to download the data. I made some judgment calls as to how i would use the data and the queries made are below.

the key data can be run in `index.js`: 

- speakers: 174
- videos: 222

## Videos

```graphql
  videoses {
    link
    views
    likes
    duration
    publishedAt
    description
    tags {
      id
      name
    }
    speaker {
      id
      name
      bio
      topics {
        id
        topic
        stage
      }
    }
  }
```

## Topics

```graphql
query foo { 
  speakerTopics {
    id
    topic
  }
}
```


## Tags

```graphql
query foo {
  tagses {
    id
    name
    videos {
      id
      name
    }
  }
}
```

## Speakers

```graphql
query foo {
  speakerses {
    id
    name
    bio
    twitter
    publishedAt
    tutorials {
      id
    }
    videoses {
      id
      link
      views
      likes
      duration
      publishedAt
      description
      tags {
        id
        name
      }
    }
  }
}
```


## Tutorials

```graphql
query foo {
	tutorials {
    id
    name
    price
    free
    link
    description
    materials
    tutorialType
    teacher {
      id
      name
      bio
      topics {
        id
        topic
      }
    }
  }
}
```