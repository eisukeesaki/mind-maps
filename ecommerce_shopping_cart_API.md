# E-commerce shopping cart API

## issues

```text

database
    tables
        products
            id
                SERIAL PRIMARY KEY
            title
                VARCHAR
            image
                VARCHAR
                ?specific type for links
        shippingcosts
            all
                INTEGER
        coupons
            id
                SERIAL PRIMARY KEY
            code
                VARCHAR
    seeders
        products
        shippingcosts
        coupons
        
web API
    Node.js
        listen to requests
            OK: endpoints
                /
                    methods
                        GET
                            route control
                                send view
                                    markup
                                    script
                /products
                    methods
                        GET
                            route control
                                query database
                                    SELECT FROM products
                                send resource representation
                                    JSON format
                /shippingcosts
                    methods
                        GET
                            route control
                                query database
                                send resource representation
                /coupons
                    methods
                        POST
                            route control
                                query database
                                    SELECT FROM coupons WHERE code = req.body.couponCode
                                compare coupons
                                    requested
                                    SELECTed database record
                                send validity of coupon
                                  
UI
    markup
        HTML5
            components
                store(noun)
                    product list
                        product
                            title
                            price
                            image
                            add to cart
                cart
                    shopping cart
                        product
                            title
                            price
                            quantity
                            total number of unique products
                    summary
                        sum
                            total product price
                        shipping cost
                        coupon form
                        total cost
    script
        JavaScript
            data fetching
                products
                shipping cost
                coupon validity
            dynamic markup modification
                DOM manipulation
                    store
                        product components
                    cart
                        product component
                        summary component

```

## do later

```text

investigate

```

## initial mind maps

```text

digital shopping cart v0
    collection
        data
            associtation
                user
                products
                    product
                        title
                        price
                quantity
                    determined by user
                        input from user
                shipping cost
                    static value
                coupon
                    identifier
                    value
    function
        calculation
            total cost
                sum of product price + shipping cost - coupon value

resources
    products
        representation
            [
              {
                "title": "helmet",
                "price": 500,
                "image": "https://cloudinary.com/api/images/helmet.jpg"
               },
              {
                "title": "gloves",
                "price": 200,
                image": "https://cloudinary.com/api/images/gloves.jpg"
               }
            ]
        methods
            GET
        URI
            /products
    shipping cost
        representation
            {
              "shippingCost": 20
            }
        methods
            GET
    coupons
        representation
            {
              "couponCode": 1234
            }
        methods
            POST
    view files
        representation
            index.html
            index.js
        methods
            GET HTTP/1.1
        URI
            /

middlewares
    serveProductImage
        extract product-image-URI from product record
        make HTTP GET request to the URI
        send downloaded image as response
            express.static()

UI
    views
        index.html
            functions
                values
                    show
                        product
                            title
                            price
                            quantity
                        shipping cost
                        coupon
                    modify
                        product
                            add
                            remove
                            quantity
                    calculator
                        total cost
            components
                store(noun)
                    product list
                        product
                            title
                            price
                            image
                            add to cart
                cart
                    shopping cart
                        product
                            title
                            price
                            quantity
                            total number of unique products
                    summary
                        sum
                            total product price
                        shipping cost
                        coupon form
                        total cost

front-end script
    DOM manipulation
    HTTP requests
        fetch API

digital shopping cart vN
    integrate authentication function
    tax
    dynamic shipping cost
    checkout
```

## about my mind maps
[Acekay's information organization language](acekay_knowledge_organization_language.md)

