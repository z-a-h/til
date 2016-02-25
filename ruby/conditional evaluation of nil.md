#Conditional Evaluation of Nil

`if` in Ruby is not an OO construct 

When checking to see that something is `nil` or not Ruby is actually checking to see if the returned value is of type `NilClass`. 

An OO approach to conditionals can be applied by following a Null Object Pattern.
Create an class of nill object and initialize them with blank values for use when the other object returns nil.

```ruby
# app/models/missing_basket.rb
class MissingBasket
  def line_items
    []
  end
end

# app/controllers/baskets_controller.rb
class BasketsController < ApplicationController
  def show
    @basket = Basket.find(params[:id]) || MissingBasket.new
  end
end

# app/views/baskets/show.html.erb
<% @basket.line_items.each do |item| %>
  <p><%= item %></p>
<% end %>
```
[source](http://purinkle.co.uk/post/139843782736/on-the-if)