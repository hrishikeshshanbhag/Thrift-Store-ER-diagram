# Thrift-Store-ER-diagram
A ER diagram for thrift store 
Tried to minimize tables

# A Eraser.io code
<pre>
// customer

customers [icon:user,color: blue]{
  id serial pk
  email unique not null
  name text
  password text

  created_at timestamps
  updated_at timestamps
}

// product
products[icon:book,color:green]{
  id serial pk
  price number not null
  stock int not null
  type enum(thrifted,handmade)
  condition enum[fair,good,excellent]
  category varchar(15) not null
  color varchar(15)
  size number not null
  created_at timestamps
  updated_at timestamps
}


//shipping
shipping[icon:car,color:purple]{
  id serial pk
  address text not null
  status enum(shipped,delivered,cancelled)
  shipped_at timestamps
  delived_at timestamps
}

// order
orders [icon:package,color:orange]{
  id serial pk
  shipping_id int fk
  customer_id int fk

  ordered_at timestamps
  updated_at timestamps
}
orders.shipping_id - shipping.id
customers.id < orders.customer_id

ordered_product[icon:box,color:lightyellow]{
  id serial pk
  product_id int fk
  ordered_id int fk
  quantity int not null
  
}
orders.id < ordered_product.ordered_id
products.id < ordered_product.product_id

// payments
payments[icon:money,color:lightblue]{
  id serial pk
  status boolean
  method enum(cod,bank,card)

  ordered_id int fk
}

orders.id - payments.ordered_id
</pre>
