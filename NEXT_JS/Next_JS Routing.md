
In order to create a route in Next js project

just add a folder with a name and add page.js to it
![[Pasted image 20240411085300.png]]

now the page.js outside of the "app" folder is responsible for creating the home page i.e., for example "my-homepage.com"


Now, the file page.js in the folder "about" is responsible for creating new route like "my-homepage.com / about"
in this route, the page.js file in the about folder will be rendered!!!
___

### Navigation through routes

in order to navigate through the routes just like in the react where we use "Navlink or useNavigte", in nextjs we use "Link" for navigating through pages
![[Pasted image 20240411090057.png]]
___
### Nested Routes
![[Pasted image 20240411091803.png]]
* The folder "[slug]" is a special feature that allows us to keep multiple routes 
	
* it can be like /blog/post-1 or /blog/post-2 or /blog/something, etc
	
* the name can be anything inside the square brackets example [you] | [me] | [blogsss], etc

