# Ruby Front-End Glossary

A document designed to explain concepts through via a list of frequently spouted terms.



## Terms

- Appends
- [Partials](#partials)
- Render
- Etc



### Appends

...



### Partials

#### Definition
Partials are `haml` files containing markup abstracted from a view to be used across multiple views. This practice allows the same markup to reside in two or more places within the application. 

Their file names begin with an underscore but, when `render`ed, the underscore in the file name is ommitted. See [Rendering Partials](#rendering-partials) for an example of this. 

You may pass objects to a partial and have the partial output the object data that it recieves. 

Within `app/views/weblinc/store_front`, for example, views are grouped into folders named after their controller. Partials that can be used by views across _multiple controller groups_, like the partial that is responsible for displaying flash message errors, are placed inside `app/views/weblinc/store_front/shared/`. Partials that are shared accross multiple _views_ under the same controller group, like the Pricing partial which is only responsible for the display of a product's price, are simply placed inside that group's view directory.

#### Rendering Partials
There are two ways to render a partial in a Rails application. 

If your partial only requires __1 or less__ local variables in order to operate, you can use this method:

```haml
= render 'weblinc/store_front/products/pricing', product: product
```

This code will render the pricing partial, passing the current view's `product` object along to the partial for handling.

If your partial requires __2 or more__ local varaibles in order to operate, you would use this method instead:

```haml
= render partial: 'weblinc/store_front/products/pricing', locals: { product: product, sale: true }
```

This effectually produces the same results as the first example, except it allows you to pass more than one explicitly named objects to the partial.

#### When to Use
Anytime you notice redundancy within your application, you should abstract the code into a partial. Redundancy, in this case, is defined as "the same markup being explicitly written out within two separate views." 9 times out of 10, this markup can become a partial, reacting appropriately to the object(s) being passed to it.



### Render

#### Definition
The `render` method in Ruby on Rails does simply that, renders a bit of abstracted markup (or [partial](#partials)) within a view.

#### Rendering Partials
See the [Rendering Partials](#rendering-partials) section for more information.

#### Rendering a File Appended Partial

...


