# Nuxt 3 + Tailwind CSS + DaisyUI Personal Website
Personal blog made by [Nuxt 3](https://nuxt.com/)
Click [Link](https://requiem-blog.netlify.app/) to see the page

# Setup
Make sure to install the dependencies:
```bash
yarn install
````
## Development Server
```bash
yarn dev
```
## Production
Build the application for production:
```bash
yarn build
```
Locally preview production build:
```bash
yarn preview
```

# .env
```text
NUXT_PUBLIC_MODE="MODE"
NUXT_PUBLIC_GOOGLE_ANALYTICS_ID="GA"
NUXT_PUBLIC_BASE_URL="http:somebaseurl.com"
```

# Packages
- [tailwindcss](https://tailwindcss.com/)= Tailwind css
- [daisyui](https://daisyui.com/) - Tailwind based UI Framework
- [theme-change](https://github.com/saadeghi/theme-change) - Change theme with daisyui
- [pinia](https://nuxt.com/modules/pinia) - Client side State management
- [@nuxtjs/i18n]() - vueI18n for Nuxt 3
- [@vueuse/nuxt]() - vueuse for Nuxt 3
- [@nuxtjs/tailwindcss](https://tailwindcss.nuxt.dev/) - Tailwind setting for Nuxt 3
- [@pinia/nuxt]() - Pinia for Nuxt 3
- [dayjs]() 
- [fast-glob]() - Find all files under specific directory
- ~~[vue-gtag]()~~
- [vue-gtag-next]()
- [js-cookie]() - Control cookie
- [animate.css]() - Animation list
- [postcss-custom-properties](https://www.npmjs.com/package/postcss-custom-properties) - Fix ```nuxt Cannot start nuxt: Cannot find module 'postcss-custom-properties'``` error

## Content part
- [highlight.js]() - Add highlight for code section
- [rehype-highlight]() - Add highlight for code section (not working)
- [remark-reading-time]() - Add reading time

# :file_folder: Folder structure
See more detail with [Link](https://nuxt.com/docs/guide/directory-structure/nuxt)
```text
├─ assets/                      # Assets (Videos, fonts ...)
├─ components/                  # Components
├─ content/                     # Content ( .md, .mdx ...)
├─ layouts/                     # Layouts
├─ locales/                     # i18n locales files
├─ node_modules/                # node modules
├─ pages/                       # Pages
├─ plugins/                     # Vue Plugins (Server, Client), Automatically adjust
├─ public/                      # Assets (images ...)
├─ server/                      # Server files
│  ├─ api/                      # API, File name will be path
│  ├─ routes/                   # Generate sitemaps
├─ .eslintrc.js                 # Eslint.
├─ .gitignore                   # gitignore.
├─ nitro.config.ts              # Nitro build config.
├─ app.vue                      # App vue file
├─ app.config.ts                # App config
├─ nuxt.config.ts               # Nuxt 3 config
├─ package.json                 # Package.json
├─ README.md                    # README.md
├─ tailwind.config.js           # Tailwind CSS config.
├─ tsconfig.json                # Typescript config
```

# Contributors
Thank you for helping me to make better blog

# Sites
- [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction)
- [deployment documentation](https://nuxt.com/docs/getting-started/deployment)
- [Github - Nuxt](https://github.com/nuxt/nuxt)
