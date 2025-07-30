
1. Apollo Client setup
    
2. Querying data (`useQuery`)
    
3. Using arguments & variables
    
4. Using fragments
    
5. Using aliases
    
6. Using directives
    

---

### 📦 1. Setup Apollo Client in React

####  Install dependencies:

```bash
npm install @apollo/client graphql
```

####  Create Apollo Client

```tsx
// src/apolloClient.ts
import { ApolloClient, InMemoryCache } from '@apollo/client';

const client = new ApolloClient({
  uri: 'https://api.globomantics.dev/graphql', // your GraphQL endpoint
  cache: new InMemoryCache(),
});

export default client;
```

####  Wrap your App with ApolloProvider

```tsx
// src/main.tsx or index.tsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import { ApolloProvider } from '@apollo/client';
import client from './apolloClient';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <ApolloProvider client={client}>
    <App />
  </ApolloProvider>
);
```

---

###  2. Using `useQuery` Hook

```tsx
// src/components/SpeakersList.tsx
import { useQuery, gql } from '@apollo/client';

const GET_SPEAKERS = gql`
  query GetSpeakers {
    speakers {
      id
      name
      bio
    }
  }
`;

const SpeakersList = () => {
  const { loading, error, data } = useQuery(GET_SPEAKERS);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <ul>
      {data.speakers.map((speaker: any) => (
        <li key={speaker.id}>
          <strong>{speaker.name}</strong> - {speaker.bio}
        </li>
      ))}
    </ul>
  );
};

export default SpeakersList;
```

---

###  3. Using **Arguments & Variables**

```tsx
const GET_SPEAKER_BY_ID = gql`
  query GetSpeaker($id: Int!) {
    speaker(id: $id) {
      id
      name
      bio
    }
  }
`;

const SpeakerDetails = ({ speakerId }: { speakerId: string }) => {
  const { loading, error, data } = useQuery(GET_SPEAKER_BY_ID, {
    variables: { id: speakerId },
  });

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  const speaker = data.speaker;
  return (
    <div>
      <h2>{speaker.name}</h2>
      <p>{speaker.bio}</p>
    </div>
  );
};
```

---

###  4. Using **Fragments**

```tsx
const SPEAKER_FRAGMENT = gql`
  fragment SpeakerInfo on Speaker {
    id
    name
    bio
  }
`;

const GET_ALL_SPEAKERS = gql`
  query {
    speakers {
      ...SpeakerInfo
    }
  }
  ${SPEAKER_FRAGMENT}
`;
```

Fragments help you reuse fields across queries or mutations.

---

###  5. Using **Aliases**

```tsx
const GET_KEY_SPEAKERS = gql`
  query {
    keynote: speaker(id: "1") {
      name
    }
    guest: speaker(id: "2") {
      name
    }
  }
`;

const AliasedSpeakers = () => {
  const { loading, error, data } = useQuery(GET_KEY_SPEAKERS);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <>
      <p>Keynote Speaker: {data.keynote.name}</p>
      <p>Guest Speaker: {data.guest.name}</p>
    </>
  );
};
```

---

###  6. Using **Directives** (`@include` / `@skip`)

```tsx
const GET_OPTIONAL_SPEAKER = gql`
  query GetSpeaker($id: ID!, $includeBio: Boolean!) {
    speaker(id: $id) {
      id
      name
      bio @include(if: $includeBio)
    }
  }
`;

const SpeakerWithDirective = () => {
  const { loading, error, data } = useQuery(GET_OPTIONAL_SPEAKER, {
    variables: { id: "1", includeBio: false },
  });

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <div>
      <h2>{data.speaker.name}</h2>
      {data.speaker.bio && <p>{data.speaker.bio}</p>}
    </div>
  );
};
```

---

```js
query{
  userById (id:1){
    id,
    name,
    posts (first: 3){
      title
    }
  }
}
```

`(first: 3),(id:1)` is from available arguments from the query

---
###  7. **Mutation**

```jsx

import { gql, useMutation } from '@apollo/client';

const CREATE_POST = gql`
  mutation CreatePost($post: CreatePostInput!) {
    createPost(post: $post) {
      id
      title
    }
  }
`;

export default function CreatePostSimple() {
  const [createPost, { data, loading, error }] = useMutation(CREATE_POST);

  const handleClick = () => {
    createPost({
      variables: {
        post: {
          title: "Hello GraphQL",
          body: "This is a simple post",
          userId: 1,
        },
      },
    });
  };

  return (
    <div>
      <button onClick={handleClick}>Create Post</button>

      {loading && <p>Creating...</p>}
      {error && <p>Error: {error.message}</p>}
      {data && (
        <p>
          ✅ Created Post #{data.createPost.id}: {data.createPost.title}
        </p>
      )}
    </div>
  );
}


```
