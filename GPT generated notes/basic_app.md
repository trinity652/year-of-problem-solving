Sure! Here's a basic tutorial on how to create a React frontend that consumes API endpoints created using Django:

Step 1: Create a Django API

First, you need to create a Django API using Django REST Framework. You can create API views, serializers, and urls to define the endpoints that you want to expose.

Here's a basic example of a Django API view that returns a list of objects:

```python
from rest_framework.views import APIView
from rest_framework.response import Response
from rest_framework import status

from .models import MyModel
from .serializers import MyModelSerializer

class MyModelList(APIView):
    def get(self, request, format=None):
        mymodels = MyModel.objects.all()
        serializer = MyModelSerializer(mymodels, many=True)
        return Response(serializer.data, status=status.HTTP_200_OK)
```

In this example, we define a view called `MyModelList` that returns a list of `MyModel` objects as serialized data using the `MyModelSerializer`. We also define the endpoint for this view using the `get` method.

Step 2: Create a React App

Next, you need to create a React app that will consume the Django API. You can use create-react-app to create a new React app.

```bash
npx create-react-app my-app
cd my-app
```

Step 3: Install Dependencies

To consume the Django API from a React app, you'll need to install the axios library.

```bash
npm install axios
```

Step 4: Make API Requests

Now you can make API requests from the React app to the Django API. In the React app, create a new file called `api.js` and define the base URL for your Django API:

```javascript
import axios from 'axios';

const baseURL = 'http://localhost:8000/api/';

const api = axios.create({
  baseURL: baseURL,
  timeout: 5000,
  headers: {
    'Content-Type': 'application/json',
  },
});

export default api;
```

This file exports an axios instance with the base URL of your Django API.

Next, create a new component in your React app called `MyComponent.js`:

```javascript
import React, { useState, useEffect } from 'react';
import api from './api';

function MyComponent() {
  const [mymodels, setMyModels] = useState([]);

  useEffect(() => {
    api.get('mymodels/')
      .then(response => {
        setMyModels(response.data);
      })
      .catch(error => {
        console.log(error);
      });
  }, []);

  return (
    <div>
      <h1>My Models:</h1>
      <ul>
        {mymodels.map((mymodel) => (
          <li key={mymodel.id}>{mymodel.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default MyComponent;
```

In this example, we use the `useEffect` hook to make an API request to the Django API when the component is mounted. We then update the `mymodels` state with the response data, which is an array of `MyModel` objects.

Finally, we render a list of `MyModel` objects using the `map` method.

Step 5: Render the Component

To render the `MyComponent` in your React app, open `App.js` and import the component:

```javascript
import React from 'react';
import MyComponent from './MyComponent';

function App() {
  return (
    <div>
      <MyComponent />
    </div>
  );
}

export default App;
```

That's it