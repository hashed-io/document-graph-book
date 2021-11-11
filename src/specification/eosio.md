# EOSIO Implementation 
For the full smart contracts, see the [Github repository](https://github.com/hashed-io/document-graph)

EOSIO (c++) implementation of the types of the Document Graph smart contract:
### ```FlexValue``` type
The ```FlexValue``` type is a variant that supports all of the common data types supported in the C++/WASM SDK for EOSIO. It stores the data as an array, where the first value is a ```uint8``` representing the index of the type in the ```typedef``` definition, followed by the actual value.

```c++
    typedef std::variant<std::monostate, 
                         eosio::name, 
                         std::string, 
                         eosio::asset, 
                         eosio::time_point,
                         std::int64_t, 
                         eosio::checksum256>
            FlexValue;
```

### ```Content``` type
The ```Content``` type is simply a ```FlexValue``` with an optional label. The smart contract also creates an alias for ```ContentGroup``` and ```ContentGroups``` to organize the lists of ```Content```. 

It is common for ```ContentGroups``` to be labeled by using a ```Content``` item with a label of ```content_group_label```.
```c++
    struct Content {
        std::string label;
        FlexValue value;
    };

    using ContentGroup = std::vector<Content>;
    using ContentGroups = std::vector<ContentGroup>;
```

#### Example Content Group serialized to json
```json
    "content_groups": [
        [
            {
                "label": "content_group_name",
                "value": [
                    "string",
                    "My Salary Content Group"
                ]
            },
            {
                "label": "salary_amount",
                "value": [
                    "asset",
                    "130.00 USD"
                ]
            },
            {
                "label": "recipient",
                "value": [
                    "name",
                    "daomember"
                ]
            }
        ]
    ]
```
    
### ```Certificate``` type
The ```Certificate``` type represents an account that is certifying, or attesting to, the content within that document. It includes the account name and optional notes for the signer. Of course, the signature from the certifier is required for creation of the certificate.

> Certificates will likely be replaced with [verifiable credentials](https://www.w3.org/TR/vc-data-model/)

```c++
    struct Certificate
    {
        eosio::name certifier;
        std::string notes;
        eosio::time_point certification_date = eosio::current_time_point();
    };
```

### ```Document``` type
The ```Document``` type stores the header information, ```ContentGroups```, and a list of ```Certificates```.

```c++
    struct Document 
    {
        std::uint64_t id;
        eosio::checksum256 hash;
        eosio::name creator;
        ContentGroups content_groups;
        std::vector<Certificate> certificates;
        eosio::time_point created_date;
        eosio::name contract;
    };
```

### Example Document serialized to json
```json
{
    "id":4965,
    "hash":"50be6cf143050a11e9db3a52ef68e10e07b07cf6cc68007ad46a14baf307c5b9",
    "creator": "bob",
    "content_groups": [
        [
            {
                "label": "content_group_name",
                "value": [
                    "string",
                    "My Content Group #1"
                ]
            },
            {
                "label": "salary_amount",
                "value": [
                    "asset",
                    "130.00 USD"
                ]
            },
            {
                "label": "referrer",
                "value": [
                    "name",
                    "friendacct"
                ]
            },
            {
                "label": "vote_count",
                "value": [
                    "int64",
                    67
                ]
            }
        ]
    ],
    "certificates":[],
    "created_date":"2021-01-12T18:21:10.000",
    "contract":"dao.hypha"
}
```

