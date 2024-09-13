This is the frame-work that is to be learned after React_JS
Next Js is the extension of React

With the help of Next js, we can make the pages load fast with the help of "server side rendering"
* in SSR, the static part of the web page is loaded at server an is given to the client's browser
* the remaining non-static i.e., the Dynamic part of the web page is given to the client's browser in the form of .js fille which the browser will download and renders on the screen 
---
### What to use NEXT js or React js
* In react js all the web page is rendered at client's browser in the form of a js file which needs to be downloaded in browser and after that all of the things are displayed
* By this, there will be so much load on the client's side but when we use Next js, most of the static part's of the webpage is already rendered in server int he form of html and given to the client's browser and the remaining dynamic part of the webpage is given to the client's browser in the form of js
* Since most of the page is already rendered so it will be easy for the browser to render the whole page 
* So, coming back the point, what should we use, for bigger projects try to use Next js and for smaller projects use React js
___
### How to create a Next js app?
* Make sure the version of the node in the system is alteast above 18
```
npx create-next-app@latest

npm run dev //to run the next project
```
![[Screenshot 2024-04-10 205900.png]]
![[Screenshot 2024-04-10 205604.png]]![[Screenshot 2024-04-10 205742.png]]

---
![[Pasted image 20240410223007.png]]The initial things that you see after an Next js project is created !!!
___
### Naming of the files
Reserved Filenames

As you already learned, there are some reserved filenames when working with NextJS.

Important: These filenames are only reserved when creating them inside of the `app/` folder (or any subfolder). Outside of the `app/` folder, these filenames are not treated in any special way.

Here's a list of reserved filenames in NextJS - you'll, of course, learn about the important ones throughout this section:

- `page.js` => Create a new page (e.g., `app/about/page.js` creates a `<your-domain>/about` page)
    
- `layout.js` => Create a new layout that wraps sibling and nested pages
    
- `not-found.js` => Fallback page for "Not Found" errors (thrown by sibling or nested pages or layouts)
    
- `error.js` => Fallback page for other errors (thrown by sibling pages or nested pages or layouts)
    
- `loading.js` => Fallback page which is shown whilst sibling or nested pages (or layouts) are fetching data
    
- `route.js` => Allows you to create an API route (i.e., a page which does NOT return JSX code but instead data, e.g., in the JSON format)

You also find a list with all supported filenames & detailed explanations in the official docs: [https://nextjs.org/docs/app/api-reference/file-conventions](https://nextjs.org/docs/app/api-reference/file-conventions)
 ![[Pasted image 20240411085003.png]]
---

[[Next_JS Components]]
[[Next_JS Routing]]
[[Next_JS Server vs client components]]
