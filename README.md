# Wildom

Wildom is a ruby based wildcard domain search API. It has a limited regular expression support.

### Version
0.0.1

### Installation [TODO]

Wildom can be installed using the following way

```sh
$ gem install wildom
```

Wildom dependens on [whoisrb](https://whoisrb.org/) and Davatz's [spreadsheet](https://spreadsheet.ch/).
Both can be installed using the following commands

```sh
$ gem install whois
$ gem install spreadsheet
```

### Usage [TODO]

To make a basic search for a domain with common TLDs
```sh
generator = Wildom::QueryGenerator.new
result = generator.generate "example.*" #=> <Query: ......>
```
Result is an `Enumerator`, so, keep in mind that for every request you make to it, a fetch and return cycle will be involved which is a slow process (since network interaction is involved). To immediately get all the results, you can convert the result into an array using the `to_a` method.

To get a list of TLDs on which the above search is made against,

```sh
Wildom::TLD.to_a #=> ["com", "net", "org", ...............]
```

A basic wildcard search can be made like this
```sh
result = generator.generate "examp[a-z]{2}\.com" #=> <Query: ......>
```

It is possible to limit the number of results by specifying `limit` like this,

```sh
result = generator.generate "examp[a-z]{2}\.com", limit: 50 #=> <Query: ......>
```

Wildom has support for `a-z`, `A-Z`, `\d` character groups and `[]`, `{}` and `?`. Nesting is not yet supported.

### Development

Want to contribute? Great! The steps are simple.

 - Fork the project
 - Create your feature/bugfix branch
 - Make your changes
 - Create a pull request

### Todos

 - Push initial commit
 - Task: API interface dummies
 - Task: Implement primary wildcard search feature with console output
 - Task: Implement spreadsheet output
 - Task: Implement domains-to-search limit
 - Task: Implement multi-threading
 - Task: Rails integration

License
----

[![CC BY-SA](https://licensebuttons.net/l/by-sa/3.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/legalcode)
