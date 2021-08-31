# Hostname Rewrites Example

In this example, you'll learn how to programmatically create unique content pages for your users with a multi-tenant infrastructure using Edge Middleware. Each user gets assigned a unique subdomain when they create their account, with the (usually paid) option to add a custom domain.

For context, here are some example pages:  
- https://hostname-1.vercel.sh/ (subdomain)
- https://hostname-2.vercel.sh/ (subdomain)
- https://hostname-3.vercel.sh/ (subdomain)
- https://hostname-vercel.com/ (custom domain)

All of these generated sites are powered by ISR (no SSR at all) so they load pretty much instantly + the inter-page transitions are lightning fast.

The example above is generated based on the following mock database:

```
const mockDB = [
    {name: "Hostname 1", subdomain: "hostname-1", customDomain: "hostname-vercel.com"},
    {name: "Hostname 2", subdomain: "hostname-2", customDomain: null},
    {name: "Hostname 3", subdomain: "hostname-3", customDomain: null},
]
```

When deploying your own clone of this example, you will need to replace the data fetching methods in `getStaticPaths` and `getStaticProps` with your own database of choice (BYOD, *Bring-Your-Own-Database*).

## How to Use

You can choose from one of the following two methods to use this repository:

### One-Click Deploy

Deploy the example using [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=next-example):

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/git/external?repository-url=https://github.com/vercel-customer-feedback/edge-middleware/tree/main/examples/hostname-rewrites&project-name=hostname-rewrites&repository-name=hostname-rewrites)

### Clone and Deploy

Download this repository via git:

```bash
git clone https://github.com/vercel-customer-feedback/edge-middleware.git
```

Execute [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app) with [npm](https://docs.npmjs.com/cli/init) or [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/) to bootstrap the example:

```bash
npx create-next-app --example edge-middleware/examples/hostname-rewrites hostname-rewrites
# or
yarn create next-app --example edge-middleware/examples/hostname-rewrites hostname-rewrites
```

Deploy it to the cloud with [Vercel](https://vercel.com/new?utm_source=github&utm_medium=readme&utm_campaign=edge-middleware-eap) ([Documentation](https://nextjs.org/docs/deployment)).

> 💡 Do note that you will need to replace the `ROOT_URL` variable in the `.env.example` file with your domain of choice and add that domain as a wildcard domain your Vercel project.