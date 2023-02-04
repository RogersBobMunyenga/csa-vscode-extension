# Create Shop App - Next.js Boilerplate Snippets

The essential collection of Snippets for creating Shopify applications when using [@kinngh/shopify-nextjs-prisma-app](https://github.com/kinngh/shopify-nextjs-prisma-app)

![Snippets snippeting](assets/snippets.gif)

## Features

Snippets to quickly create endpoints and functions in React, Next.js and relevant Shopify app code.

I selected these snippets from my regular use and code that I was writing over and over again. Instead of again including a `__templates/` directory that was causing a lot of confusion, it made more sense to create an extension for snippets instead.

## Snippets

| Snippet           | Description                                           |
| ----------------- | ----------------------------------------------------- |
| `imr`             | Import React                                          |
| `imrs`            | Import React and useState                             |
| `imrse`           | Import React, useState and useEffect                  |
| `afc`             | Create an arrow function component                    |
| `useEffect`       | Create useEffect hook                                 |
| `useState`        | Create useState hook                                  |
| `newPage`         | Create a new Polaris page with a Card                 |
| `newPageEmpty`    | Create a new Polaris page with a Card and Empty State |
| `createapi`       | Create a new endpoint for `/api`                      |
| `createproxy`     | Create a new endpoint for `/api/proxy_route`          |
| `createwebhook`   | Create a new webhook function                         |
| `createClientGql` | Create a new GraphQL Client                           |

# Expansions

## React

### imr - Import React

```javascript
import * as React from "react";
```

### imrs - Import React and useState

```javascript
import React, { useState } from "react";
```

### imrse - Import React, useState and useEffect

```javascript
import React, { useState, useEffect } from "react";
```

### afc - Create an arrow function component

```javascript
const | = (|) => {
    return ( | );
}

export default |;

```

### useEffect - Create useEffect hook

```javascript
useEffect(() => {
    |
}, []);
```

### useState - Create useState hook

```javascript
const [|, set|] = useState();
```

## Boilerplate Code

### newPage - Create a new Polaris page with a Card

```javascript
import { Page, Layout, Card } from "@shopify/polaris";

const | = (|) => {
    return (
        <>
            <Page>
                <Layout>
                    <Layout.Section>
                        <Card sectioned title="|">
                            <p>|</p>
                        </Card>
                    </Layout.Section>
                </Layout>
            </Page>
        </>
    );
};

export default |;

```

### newPageEmpty - Create a new Polaris page with a Card and Empty State

```javascript
import { Page, Layout, Card, EmptyState } from "@shopify/polaris";

const | = (|) => {
    return (
        <>
            <Page>
                <Layout>
                    <Layout.Section>
                        <Card sectioned>
                            {/* Taken from Shopify Polaris */}
                            <EmptyState
                                heading="Manage your inventory transfers"
                                action={{ content: "Add transfer" }}
                                secondaryAction={{
                                    content: "Learn more",
                                    url: "https://help.shopify.com",
                                }}
                                image="https://cdn.shopify.com/s/files/1/0262/4071/2726/files/emptystate-files.png"
                            >
                                <p>Track and receive your incoming inventory from suppliers.</p>
                            </EmptyState>
                        </Card>
                    </Layout.Section>
                </Layout>
            </Page>
        </>
    );
};

export default |;

```

### createapi - Create a new endpoint for `/api`

```javascript
import withMiddleware from "@/utils/middleware/withMiddleware.js";

const | = async (req, res) => {
    if (req.method === "GET") {
        //GET, POST, PUT, DELETE
        console.log("Serve this only if the request method is GET");
    }

    try {
        |
        return res.status(200).send({ text: "Success!" });
    } catch (e) {
        console.error(e);
        return res.status(400).send({ text: "Bad request" });
    }
};

export default withMiddleware("verifyRequest")(|);
```

### createproxy - Create a new endpoint for `/api/proxy_route`

```javascript

import withMiddleware from "@/utils/middleware/withMiddleware.js";

const | = async (req, res) => {
    if (req.method === "GET") {
        //GET, POST, PUT, DELETE
        console.log("Serve this request only if method type is GET");
    }
    try {
        |
        res.status(200).send({ content: "Proxy Be Working" });
    } catch (e) {
        console.error(e);
        res.status(400).send({ content: "An error occured" });
    }
};

export default withMiddleware("verifyProxy")(|);
```

### createwebhook - Create a new webhook function

```javascript
const | = async (topic, shop, webhookRequestBody, webhookId, apiVersion) => {
    try {
        const webhookBody = JSON.parse(webhookRequestBody);
        |
    } catch (e) {
        console.error(e);
    }
};

export default |;
```

### createClientGql - Create a new GraphQL Client

```javascript
import clientProvider from "@/utils/clientProvider";
import withMiddleware from "@/utils/middleware/withMiddleware";

const | = async (req, res) => {
    try {
        const { client } = await clientProvider.graphqlClient({
            req,
            res,
            isOnline: |, //false for offline session, true for online session
        });

        const response = await client.query({
            data: `{}`, //Paste your GraphQL query/mutation here
        });

        res.status(200).send(response);
    } catch (e) {
        console.error(e);
        res.status(400).send({ error: "An error occured" });
    }
};

export default withMiddleware("verifyRequest")(|);
```
