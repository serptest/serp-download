## Installation

<Steps>
### Step 1: Install

```npm
npm install @openpanel/web
```

### Step 2: Initialize

```js title="op.ts"


const op = new OpenPanel({
  clientId: 'YOUR_CLIENT_ID',
  trackScreenViews: true,
  trackOutgoingLinks: true,
  trackAttributes: true,
});
```

#### Options

<CommonSdkConfig />
<WebSdkConfig />

### Step 3: Usage

```js title="main.ts"


op.track('my_event', { foo: 'bar' });
```
</Steps>

## Usage

Refer to the [Javascript SDK](/docs/sdks/javascript#usage) for usage instructions.
