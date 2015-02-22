Name Machine
-----------------------

[![Join the chat at https://gitter.im/ajbrown/NameMachine](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/ajbrown/NameMachine?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Build Status](https://travis-ci.org/ajbrown/NameMachine.svg?branch=develop)](https://travis-ci.org/ajbrown/NameMachine)


Name machine is a Java utility for generating random names with realistic probabilities of occurrence.  In other words,
names that occur more often in real life will also occur more often in the random generation.


It's lightweight, and has no dependencies.  It loves being used to generate sample data for tests and demos!


```java
NameGenerator generator = new NameGenerator();

// generate 1000 female names
List<Name> names = generator.generateNames( 1000, Gender.FEMALE );


// generate 5000 male and female names.
List<Name> names = generator.generateNames( 5000 );
```

It can also be run on the command line to output random numbers:

```bash

java -jar NameMachine.jar 1000 females

java -jar NameMachine.jar 5000

```


#### Limitations

- Name generation is bound to integer max, so you can only generate integer max names in one pass.  If you need more,
 just make more passes.


#### How Does it Work?

The name files used to generate random names are provides by the 1990 U.S. Census data.  The originals are [available on the web]
(http://www.census.gov/topics/population/genealogy/data/1990_census/1990_census_namefiles.html).  Along with the
names in ranked order is the Frequency in percent, Cumulative frequency in percent, and the rank.

We randomly select a name from the list by generating a random floating point number, and picking the first name that has a higher or equal
cumulative frequency than our random number.
