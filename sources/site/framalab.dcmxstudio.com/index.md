---
title: "Framalab SDK"
sidebarTitle: "Home"
description: "Build your custom photo gallery frontend using approved photos from your Framalab project."
---

The Framalab SDK is a zero-dependency TypeScript client for the Gallery API. It gives developers typed access to a project's approved photos — collections, versions, and on-demand image transforms — so you can build the gallery frontend in any stack you choose.

<Info>
  Looking for the Framalab panel? Go to [framalab.dcmxstudio.com](https://framalab.dcmxstudio.com). This documentation is for developers building gallery frontends with the SDK.
</Info>

## Get started in four steps

<Steps>
  <Step title="Install the SDK">
    ```bash
    pnpm add @framalab/sdk
    ```
  </Step>
  <Step title="Get a gallery token">
    In your Framalab panel, open the project, go to **Settings → Gallery**, and click **Generate token**. Copy it immediately — it is shown only once.
  </Step>
  <Step title="Initialize the client">
    Store both values as environment variables — never hardcode them in source.

    ```env .env.local
    FRAMALAB_URL=https://panel.yourdomain.com
    FRAMALAB_TOKEN=your-gallery-token
    ```

    ```ts
    import { createFramalabClient } from "@framalab/sdk"

    const client = createFramalabClient({
      baseUrl: process.env.FRAMALAB_URL!,
      token: process.env.FRAMALAB_TOKEN!,
    })
    ```
  </Step>
  <Step title="Fetch your first photos">
    ```ts
    const photos = await client.getPhotos()
    const thumb = photos[0]?.versions.find(v => v.versionType === "webp_thumb")
    console.log(thumb?.url)
    ```
  </Step>
</Steps>

## Explore the docs

<CardGroup>
  <Card title="Quickstart" icon="bolt" href="/get-started/quickstart">
    Install the SDK, initialize the client, and fetch your first photos in under 5 minutes.
  </Card>
  <Card title="SDK Reference" icon="code" href="/sdk/create-framalab-client">
    Full reference for all five SDK methods with types and examples.
  </Card>
  <Card title="Authentication" icon="key" href="/concepts/authentication">
    How gallery tokens work and how to store them safely.
  </Card>
  <Card title="Examples" icon="rectangle-terminal" href="/examples/nextjs">
    Full implementations for Next.js App Router and Astro.
  </Card>
</CardGroup>