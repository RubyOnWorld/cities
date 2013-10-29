# Cities

All the cities of the world (according to the periodically updated MaxMind.com database).

## Data

To use this gem, you'll need the JSON data.

Download it, extract it and connect it up as follows.

```
$ wget https://s3-us-west-2.amazonaws.com/cities-gem/cities.tar.gz
$ tar -zxvf cities.tar.gz
```

```ruby
City.data_path = '/path/to/cities'
```

## Usage

Countries are identified by their [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) codes.

```ruby
cities = City.cities_in_country("GB")
  #=> { "abberley"=> #<City:0x000001049b9ba0>, "abberton"=> #<City:0x000001049b9b50>, ... }

mcr = cities["manchester"]
  #=> #<City:0x00000102fb4ea8>

mcr.name
  #=> "Manchester"

mcr.population
  #=> 395516

mcr.latlong
  #=> [53,5, -2.216667]
```

The database is exhaustive and certainly stretches the definition of the word "city".

```ruby
City.cities_in_country("GB")["buchlyvie"].population
  #=> 448
```

## Countries gem

This gem was designed as an extension to the [Countries gem](https://github.com/hexorx/countries).

```
$ gem install countries
```

Search for cities through a Country:

```ruby
us = Country.search("US")
  #=> #<Country:0x000001020cf5f0>

us.cities
  #=> { "abanda" => #<City:0x00000114b34a38>, ...  }

us.cities.length
  #=> 85964
```

This product includes data created by MaxMind, available from http://www.maxmind.com

All data provided copyright (c) 2008 MaxMind Inc.

## License 

Released under an MIT license (see LICENSE.txt).

Thanks to [hexorx](https://github.com/hexorx) for the countries gem that brought this idea about.
