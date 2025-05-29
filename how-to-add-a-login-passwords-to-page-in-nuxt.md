# How to add username/password authentication to a page in Nuxt

<br><br>

<a href="https://www.youtube.com/watch?v=E5fou1hbApE" target="_blank">
<img src="https://raw.githubusercontent.com/devinschumacher/uploads/refs/heads/main/images/protecting-a-route-with-password-authentication-in-nuxt.jpg" width="700px">
</a>

<br><br>

nuxt-security provides middleware to easily add login/pass authentication to any route in Nuxt via [Basic Auth](https://nuxt-security.vercel.app/middleware/basic-auth).

Only users with correct credentials passed to the browser prompt will be able to see the application. Others will be automatically rejected.

This middleware is disabled by default. You can enable it globally like following:

1. Install [nuxt-security](https://nuxt-security.vercel.app/)
2. Enable basic auth in nuxt.config.ts
```ts
export default defineNuxtConfig({
  security: {
    basicAuth: {
      // options
    }
  }
})
```

Basic Auth accepts following configuration options:
```ts
type BasicAuth = {
  exclude?: string[];
  include?: string[]; // Paths to include in Basic Auth functionality.
  name: string; // User name that is required for user/pass flow
  pass: string; // User password that is required for user/pass flow
  enabled: boolean; // Boolean value to indicate whether a BasicAuth is enabled or not.
  message: string;
}
```

## Example

Let's say you want to password protect a page on your website `site.com/clients-i-hate`
```ts
export default defineNuxtConfig({
  security: {
    basicAuth: {
      include: '/clients-i-hate',
      name: 'youLoginUsername',
      pass: 'thePasswordYouChose',
      enabled: 'true',
    }
  }
})
```

And when a visitor tries to reach the page, they will get this: 

![image](https://github.com/user-attachments/assets/b1442ee8-408f-475a-8558-f170824c70ec)


