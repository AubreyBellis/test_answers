# test_answers

##Software Engineering Test##

####***Question 1***####
```
class Country < ActiveRecord::Base
    has_many :cities
  end 
  ```
```
class City < ActiveRecord::Base
  belongs_to :country
  has_many :bars
end
```
```
class Bar < ActiveRecord::Base
  belongs_to :city
end
```
(Please feel free to use any documentation you can find)

How would you (in a controller method) assign to @country the Country named ‘France’?

```
@country = Country.find_by_name('France')

```


How would you assign to @cities an Array of all the cities in France?

```
//find the country France again
@country = Country.find_by_name("France")

//show all cities that belong to France
@cities = @country.cities

```

How would you assign to @bars an Array of all the bars in France?

```

//find the country France again
@country = Country.find_by_name("France")

//find all the cities that belong to france 
@cities = @country.cities

//create an empty array for bars
@bars = []

//loop through each city in France, find bars that belong to that city  
@cities.each do |city|
   @bars << city.bars
```

How would you assign to @directory an Array of the names of all the bars in France, sorted?
```
//first create an empty directory array to push too
@directory = []
//find your country and it's cities again
@country = Country.find_by_name("France")
@cities = @country.cities

//for each 'city bar' push bar.name in directory
@cities.each do |city|
  city.bars.each do |bar|
    @directory << bar.name
```


Do any of the above answer change if there are 400 cities? No. 


How about if there are 20,000 bars? No. 


####***Question 2***####

Let S be the set of numbers greater than zero and less than 100,000
that are evenly divisible by 19.

```
   @numbers = []
    (1...100000).each do |num|
      if num % 19 == 0
        @numbers << num
```

How many numbers are there in S? (5263)
```
@numbers.count
```

How many numbers in S have a square that ends in a 1? 

```
    counter = 0
    @numbers.each do |num|
      sqrt = Math.sqrt(num)
      if sqrt.end_with?("1")
        counter +=1
```

How many numbers in S have a reflection that is also in S? (The reflection of 145 is 541) 280

How many numbers in S can be multiplied by some other number in S to produce a third number in S?

####***Question 3***####

An ant is walking on the squares of a 5x5 grid - it starts in the center square.

Each second, it will choose (with equal probability)
to do one of the following:

- Move north one square
- Move south one square
- Move east one square
- Move west one square
- Do not move

If it cannot perform the action it has decided on (move west while on the 
west edge, for example), it sits in place.

After one second, it has a 20% chance of being in the center, and a 20% chance
of being in each adjacent square. (and a 0% chance of being in any
other square on the board).

You may ignore floating point error accumulation.
Questions:

What is the probability that the ant is on the center square after 15 seconds?

What is the probability that the ant is on one of the outermost squares after 1 hour?