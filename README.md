# tauri-sveltekit-template

Minimal template for building cross-platform desktop applications with [Tauri](https://tauri.studio/) and [SvelteKit](https://kit.svelte.dev/).

## Setting up
1. Set up your development environment for Tauri: https://tauri.studio/en/docs/getting-started/intro

2. Install Tauri CLI
    ```bash
    cargo install tauri-cli --version ^1.0.0-beta
    ```

3. Set up your project
    ```bash
    cd your-project
    npm install
    ```

## Development
```bash
cargo tauri dev
```

## Building
```bash
cargo tauri build --verbose
```

## How to set up from scratch

Here is a step-by-step guide on how to set up a project
like this from scratch.

1. Firstly, complete the first two steps in [Setting up](#setting-up)

2. [Initialize a new SvelteKit app](https://kit.svelte.dev/docs)
    ```bash
    npm init svelte@next my-app
    # Which Svelte app template? » Skeleton project
    # Use TypeScript? » Yes
    # Add ESLint for code linting?  » Yes
    # Add Prettier for code formatting?  » Yes
    cd my-app
    npm install
    ```

3. Install additional dependencies
    ```bash
    npm install @tauri-apps/api @sveltejs/adapter-static@next
    ```

4. Configure svelte.config.js
   ```javascript
    // Add this to the imports
    import adapter from '@sveltejs/adapter-static';

    // Add this under config.kit
    adapter: adapter({
        pages: 'build',
        assets: 'build'
    }),
   ```
5. Initialize a Tauri project
    ```bash
    cargo tauri init
    # Where are your web assets located? » ../build
    # What is the url of your dev server? » http://localhost:3000
    ```

6. Configure `src-tauri/tauri.conf.json`
   - Set `beforeDevCommand` to `npm run dev`
   - Set `beforeBuildCommand` to `npm run build`
7. Test it out
    ```bash
    cargo tauri info
    cargo tauri dev
    ```