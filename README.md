# oneRing
## _An API SDK/Client for Lord of the Rings API_

This is a python3 library sdk for interfacing with a publically available Lord of The Rings API.

- Supports almost all of the original features of the API.
- The only unsupported feature is: **exists, doesn't exists**

## Installation

oneRing requires [python3 requests](https://pypi.org/project/requests/) to run.

Install oneRing from PyPI.

```
pip install oneRing-SDK
```

# Usage

Instantiate the OneRing Client:

- Instantiating the OneRing Client requires an API key from https://the-one-api.dev/. Create an account there to grab your API key, and pass it as an argument to the Client constructor like below:

```
client = OneRing.Client(<your_api_key>)
```

Make a request using one of the many client methods:
```
client.getBook()
```
or
```
client.getBookById('5cf5805fb53e011a64671582')
```

You can also pass in more complicated queries to access the more advanced features of the original API:

```
characterQuery = {'race': { 'operator': '=', 'value': 'Hobbit,Human' },
                  'sort': { 'criteria': 'name', 'order': 'desc'} }
client.getAllCharacters(characterQuery)
```

The above example will get all characters, that have a race of Hobbit or Human, and will sort the results by name in descending order.
Providing the sort options is optional and not required.

In this way, you can also have more combinations of queries like so:

```
characterQuery = { 'race': { 'operator': '=', 'value': 'Hobbit,Human' },
                   'gender': {'operator': '=', 'value': 'Male' },
                   'limit' : {'operator': '=', 'value': '3'},
                   'sort': { 'criteria': 'name', 'order': 'desc'} }
client.getAllCharacters(characterQuery)
```

This should work with any of the supported query-types of the original API.

# Testing

To test the responses of the API, you can do the following:

```

characterQuery = { 'race': { 'operator': '=', 'value': 'Hobbit,Human' },
                   'gender': {'operator': '=', 'value': 'Male' },
                   'limit' : {'operator': '=', 'value': '3'},
                   'sort': { 'criteria': 'name', 'order': 'desc'} }
jsonData = client.getAllCharacter(characterQuery)
print(json.dumps(jsonData, indent=4))
```

This will print out the entire response object returned from the underlying api. This applies to any of the client methods, they all return the raw json returned from the underlying API.

# List of Client methods with examples:

- client.getAllCharacters()
- client.getCharacterById('5cdbe3667ed9587226e7949e')
- client.getCharactersByName('Figwit')
- client.getCharacterQuotes('5cdbe3667ed9587226e7949e')
- client.getAllQuotes()
- client.getQuoteById('5cd96e05de30eff6ebccebca')
- client.getAllChapters()
- client.getChapterById('6091b6d6d58360f988133bc6')
- client.getChapterByName("Homeward Bound")
- client.getAllChaptersOfBook('5cf58080b53e011a64671584')
- client.getAllBooks()
- client.getBookById('5cf5805fb53e011a64671582')
- client.getBookByName('The Fellowship Of The Ring')

## License

MIT
