- Laravel version 6.2
- Database MySQL
- PHP version 7.4
- Database name : cashiers
- API Auth using JWT Auth
- After create database, execute 'cashiers.sql' file to create database structure

API List:
- POST Register 
curl --location --request POST 'localhost:8000/api/register' \
--data-raw '{
    "name":"lorem ipsum",
    "email":"lorem@mail.com",
    "password":"pass1234",
    "password_confirmation":"pass1234"
}'

- POST Login - Get token
curl --location --request POST 'localhost:8000/api/login' \
--data-raw '{
    "email":"johndoe@mail.com",
    "password":"password"
}
'

- GET Get transaction list (AUTHORIZATION Bearer Token)
curl --location --request GET 'localhost:8000/api/get-transaction'

- GET Get transaction detail by id (AUTHORIZATION Bearer Token)
curl --location --request GET 'localhost:8000/api/get-transaction/28'

- POST Create new transaction (AUTHORIZATION Bearer Token, BODY raw)
curl --location --request POST 'localhost:8000/api/store-transaction' \
--data-raw '{
    "summary": [
        {
            "total_amount": 25000,
            "paid_amount": 25000,
            "change_amount": 0,
            "payment_method": "card"
        }
    ],
    "items": [
        {
            "title": "barang 1",
            "qty": 1,
            "price": 10000
        },
        {
            "title": "barang 2",
            "qty": 1,
            "price": 15000
        }
       
    ]
}'

- PUT Delete transaction (AUTHORIZATION Bearer Token)
curl --location --request PUT 'localhost:8000/api/delete-transaction/3'

- PUT Update transaction (AUTHORIZATION Bearer Token, BODY raw)
curl --location --request PUT 'localhost:8000/api/update-transaction/26' \
--data-raw '{
    "summary": [
        {
            "total_amount": 6000,
            "paid_amount": 10000,
            "change_amount": 4000,
            "payment_method": "cash"
        }
    ],
    "items": [
        {
            "title": "goods 1",
            "qty": 3,
            "price": 1000
        },
        {
            "title": "goods 2",
            "qty": 1,
            "price": 3000
        }
    ]
}'
