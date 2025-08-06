This presentation is built using [Slidev](https://sli.dev). 
We can use markdown as the base layout, CSS to modify the layout, and
KaTeX to write matheamtics formulation.

## Installation 

### Linux

1. Install `nvm=22.14.0`

2. Install `pnpm=10.13.1`. It is not recommended to use `npm`, because it will 
   download the package each time we create a new project , which is slow and
   take up a lot of space
   ```
   npm i -g pnpm
   ```

3. [only for the slide creation] Install the latest `slidev`   
   ```
   pnpm create slidev
   ```

4. Copy this repo, and install the required npm packages
   ```
   npm init
   ``` 

5. Start slidev
   ```
   npm run dev
   ```

   