<template>
  <div>
    <h1>Hola Nuxt</h1>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum, asperiores magni? A similique exercitationem quos, doloribus eligendi perspiciatis consectetur eum, doloremque sed quae
      rat, ea quidem possimus nihil veniam vero commodi!</p>

    {{ course }}
  </div>
</template>

<script>
import gql from 'graphql-tag'
const character = gql`
      query getCharacters {
        characters {
          results {
            id
            name
          }
        }
      }
    `

const course = gql`
    query getSingleCourse {
      course(id:2) {
        title
        author
        description
        topic
        url
      }
    }
` 
export default {
  apollo: {
    $loadingkey: 'loading',
    course: {
      query: course
    }
  }
};
</script>