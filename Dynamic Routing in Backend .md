# Dynamic Routing - Make Your Website Flexible
Dynamic Routing allows a website to show different content using the same route structure.
instead of creating a seperate page for every URL, dynamic routes load content based on the URL.
## Real Life Analogy
Postman delivering letters to houses with different numbers.
- Road ( Route) = Same
- House Numbers (Parameters) = Different
- House Number changes exact delivery (Content)

## Visual Image for Understanding:

![dynamic_routing](https://github.com/user-attachments/assets/26aa0767-653a-4a46-9481-f47f3ba0fcd8)

- here, localhost:3000/secondPage = static part
- /1 , /2 , /3 = Dynamic Part which show different content based on the URL

## Easy Working Flow

### User -> Enters URL -> /profile/:id -> Router reads :id value -> Fetch content based on :id -> Render page dynamically
                 
