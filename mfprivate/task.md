# Mädchenflohmarkt Android Coding Challenge

## Impress us with a product viewer app!

We’d like to ask you to implement a little Android app that allows showing information about some items from our service. The app should support devices with API 19 or newer and support landscape and portrait orientation. The app should have 2 screens:

- The **product listing** displays a list of products with short product overview like name, price and some kind of indication if the product is concierge or not (see data model description). For concierge items use red text and black for regular items. On user tap the next screen should be opened with more detailed information about the selected product.
- The **product page** displays at least one product image, name, description, brand, category, price, shipping cost and “open in browser” button. Also, this screen should display the user's username and photo (shown in circular shape).

Please use this repository to store your code. Commit and push often to separate logical steps. We would like to see in the git history how you proceeded.

## The app algorithm

On each app start, it should load the root model. In the root model at path `links.products` you can find an array with links to products feeds. Please, use the first link in the array if it is available. By fetching this link you can get a json object with many properties, where:
- `links.next` – link to next product page. Could be null (this means that there is no next page). Please implement infinitive loading based on this.
- `products` – array with products. Could be empty.

The product model has many values. You can use any values but some links could return a 404 error. The most interesting fields for this project:
- `links.base` – string. link to full product information. (A product model fetched fron this link has user data.)
- `links.websiteUrl` – string. link for "open in browser". Should open the website in an embedded browser or in external.
- `concierge` – bool value. Required to use alternative text color.
- `name` – string. Product name.
- `description` – string. Product description.
- `brand.name` – string. Brand name.
- `category.name` – string. Category name.
- `price` – number. Product price in EURO.
- `priceShipping` – number. Product shipping cost in EURO.
- `images` – an array of the image objects. Each image object has 3 important fields:
  - `width` and `height` – number. original image size. Could be used to calculate the image’s aspect ratio.
  - `url` – string. Universal image link. **Important!** You should replace strings `_WIDTH_` and `_HEIGHT_` with real required image size. E.g. `https://mfcdn.de/product/_WIDTH_x_HEIGHT_/tunika-bluse-h-m-cf96a9.jpeg` must be transformed to something like `https://mfcdn.de/product/260x195/tunika-bluse-h-m-cf96a9.jpeg`.

A full product model has a `user` property. This model has:
- `username` – string. Visible username
- `photo` – string. Link to profile image. Always square. Link could be to an internal resource with `_WIDTH_x_HEIGHT_` or to an external resource, e.g. facebook. This value could be null.

## Api

### root model

The root model with all information required for the app work. It has an array of possible feeds.
`https://prelved.app/v1/root.json`. Always use this url in the test project.

### products feed

Feed with products and other information, like pagination and others.
`https://prelved.app/v1/:feedId.json`
Example data https://prelved.app/v1/products.json
Hint: don't hardcode this. Take it from the responses you get from the backend.

### Full product model

Product model with user information.
`https://prelved.app/v1/products/:productId.json`
Example data https://prelved.app/v1/products/3806090.json

## Some optional tasks

They are not required, but it would be nice if you could find some time to do it:

- Add product image to the product list.
- Use a grid layout in the product's list.
- Show all available images in the product detail page.
- Display any extra useful information product details.

## Time limitation

You have 2 hours to complete it and send it back to us. Don't worry if you haven't had enough time to complete this task. We would like to ask you to spend another 15 minutes and write us an [email](mailto:andreas@maedchenflohmarkt.de?cc=vasyl@maedchenflohmarkt.de&subject=Mädchenflohmarkt%20Android%20Remote%20Case). It would be nice if you could describe the difficulties you faced during the implementation, the ideas which you wanted to implement but couldn't, if you had done, you would have done in a real project. Feel free to write us any feedback and opinions about this test task.
