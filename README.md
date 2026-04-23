# Kameleoon JavaScript SDK

## Introduction

Kameleoon JavaScript SDK is used to work with Kameleoon Feature Flags and Experiments using native JavaScript api.
Integration of this SDK into web application is easy, and its footprint is low.

This page describes the most basic `KameleoonClient` configuration, for more in-depth review of all the methods and configuration options follow [Official Kameleoon Documentation](https://developers.kameleoon.com/javascript-sdk.html)

## Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage Example](#usage-example)
- [External Dependencies](#external-dependencies)

## Installation

- **npm** - `npm install @kameleoon/javascript-sdk`
- **yarn** - `yarn add @kameleoon/javascript-sdk`
- **pnpm** - `pnpm add @kameleoon/javascript-sdk`
- **bun** - `bun install @kameleoon/javascript-sdk`

## Configuration

1. Obtain your site code from [Kameleoon Platform](https://app.kameleoon.com/)
2. Create client instance

```ts
import { KameleoonClient } from '@kameleoon/javascript-sdk';

const client = new KameleoonClient({ siteCode: 'my_site_code' });
```

## Usage Example

```ts
// -- Wait for the client initialization
await client.initialize();

// -- Generate or obtain a visitor code
const visitorCode = KameleoonClient.getVisitorCode();

// -- Add targeting data
const customDataIndex = 0;
client.addData(visitorCode, new CustomData(customDataIndex, 'my_data'));

// -- Check if the feature flag is active
const isActive = client.isFeatureFlagActive(visitorCode, 'my_feature_key');
```

## External Dependencies

JavaScript SDK utilizes certain external dependencies, which are required to be able to use specific APIs.

There are several possible external dependencies used by Kameleoon JavaScript SDK, all of them have built-in implementation in SDK but can optionally be implemented by a developer using an SDK.

Here is the list of such dependencies:

- `visitorCodeManager` is responsible for managing the visitor code and cookies
- `eventSource` is responsible for Real Time Updates(Streaming) for SDK
- `storage` is responsible for storing all SDK related data

Following is the example implementation for each dependency.

### visitorCodeManager

```ts
import {
  KameleoonClient,
  IExternalVisitorCodeManager,
} from '@kameleoon/javascript-sdk';

class MyVisitorCodeManager implements IExternalVisitorCodeManager {
  // - Get visitor code from browser cookies
  public getData(key: string): string | null {
    const cookieString = document.cookie;

    const cookieEntry = cookieString.split(' ;').find((keyValue) => {
      const [cookieKey, cookieValue] = keyValue.split('=');

      return cookieKey === key && cookieValue !== '';
    });

    if (cookieEntry) {
      const [_, value] = cookieEntry.split('=');

      return value;
    }

    return null;
  }

  // - Set visitor code back to browser cookies
  public setData({
    visitorCode,
    domain,
    maxAge,
    key,
    path,
  }: SetDataParametersType): void {
    let resultCookie = `${key}=${visitorCode}; Max-Age=${maxAge}; Path=${path}`;

    if (domain) {
      resultCookie += `; Domain=${domain}`;
    }

    document.cookie = resultCookie;
  }
}

const client = new KameleoonClient({
  siteCode: "my_site_code",
  externals: {
    visitorCodeManager: new MyVisitorCodeManager();
  }
});
```

### eventSource

```ts
import { KameleoonClient, IExternalEventSource } from '@kameleoon/javascript-sdk';

class MyEventSource implements IExternalEventSource {
  private eventSource?: EventSource;

  public open({
    eventType,
    onEvent,
    url,
  }: EventSourceOpenParametersType): void {
    // - Use any suitable EventSource implementation here
    const eventSource = new EventSource(url);

    this.eventSource = eventSource;
    this.eventSource.addEventListener(eventType, onEvent);
  }

  public close(): void {
    if (this.eventSource) {
      this.eventSource.close();
    }
  }
}

const client = new KameleoonClient({
  siteCode: "my_site_code",
  externals: {
    eventSource: new MyEventSource();
  }
});
```

### storage

```ts
import { KameleoonClient, IExternalStorage } from '@kameleoon/javascript-sdk';

const storage = new Map();

class MyStorage<T> implements IExternalStorage<T> {
  public read(key: string): T {
    // - Utilize the storage implementation of your choice
    const data = storage.get(key);

    // - Optionally handle errors
    if (!data) {
      throw new Error("Couldn't read data from myStorage");
    }

    return data;
  }

  public write(key: string, data: T): void {
    storage.set(key, data);
  }
}

const client = new KameleoonClient({
  siteCode: "my_site_code",
  externals: {
    storage: new MyStorage();
  }
});
```
