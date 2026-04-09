## Installation

<Steps>
### Step 1: Install

```npm
npm install @openpanel/sdk
```

### Step 2: Initialize

```js title="op.ts"


const op = new OpenPanel({
  clientId: 'YOUR_CLIENT_ID',
  clientSecret: 'YOUR_CLIENT_SECRET',
});
```

#### Options

<CommonSdkConfig />

### Step 3: Usage

```js title="main.ts"


op.track('my_event', { foo: 'bar' });
```
</Steps>

## Usage

### Tracking Events

You can track events with two different methods: by calling the `op.track( directly or by adding `data-track` attributes to your HTML elements.

```ts title="index.ts"


op.track('my_event', { foo: 'bar' });
```

### Identifying Users

To identify a user, call the `op.identify( method with a unique identifier.

```js title="index.js"


op.identify({
  profileId: '123', // Required
  firstName: 'Joe',
  lastName: 'Doe',
  email: 'joe@doe.com',
  properties: {
    tier: 'premium',
  },
});
```

### Setting Global Properties

To set properties that will be sent with every event:

```js title="index.js"


op.setGlobalProperties({
  app_version: '1.0.2',
  environment: 'production',
});
```

### Incrementing Properties

To increment a numeric property on a user profile.

- `value` is the amount to increment the property by. If not provided, the property will be incremented by 1.

```js title="index.js"


op.increment({
  profileId: '1',
  property: 'visits',
  value: 1 // optional
});
```

### Decrementing Properties

To decrement a numeric property on a user profile.

- `value` is the amount to decrement the property by. If not provided, the property will be decremented by 1.

```js title="index.js"


op.decrement({
  profileId: '1',
  property: 'visits',
  value: 1 // optional
});
```

### Working with Groups

Groups let you track analytics at the account or company level. See the [Groups guide](/docs/get-started/groups) for the full walkthrough.

**Create or update a group:**

```js title="index.js"


op.upsertGroup({
  id: 'org_acme',
  type: 'company',
  name: 'Acme Inc',
  properties: { plan: 'enterprise' },
});
```

**Assign the current user to a group** (call after `identify`):

```js title="index.js"


op.setGroup('org_acme');
// or multiple groups:
op.setGroups(['org_acme', 'team_eng']);
```

Once set, all subsequent `track()` calls will automatically include the group IDs.

### Clearing User Data

To clear the current user's data (including groups):

```js title="index.js"


op.clear()
```
