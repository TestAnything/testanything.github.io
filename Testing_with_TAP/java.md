---
layout: default
title: Testing with Java
---

# Testing with Java

## Testing using tap4j

### Installation

In order to install tap4j you have to download a jar from (http://tap4j.sourceforge.net)[http://tap4j.sourceforge.net] or if you are a Maven user you can add a dependency in your pom.xml, as shown below.

```
<dependency>
 <groupid>br.eti.kinoshita</groupid>
 <artifactid>tap4j</artifactid>
</dependency>
```

Differently than in others implementations, tap4j uses an Object Oriented approach. Instead of calling methods like ok(), not_ok(), is() and isnt(), you construct objects such as a TAP Producer to dump TAP and a TAP Consumer to load TAP. A [TestSet](http://tap4j.sourceforge.net/apidocs/org/tap4j/model/TestSet.html) object is used to encapsulate all the TAP Elements.

## Generating TAP using a TAP Producer

The TAP Producers in tap4j are created using a [TapProducerFactory](http://tap4j.sourceforge.net/apidocs/org/tap4j/producer/TapProducerFactory.html). After a TAP Producer is created we can call the dump method passing a [TestSet](http://tap4j.sourceforge.net/apidocs/org/tap4j/model/TestSet.html) to have the result TAP.

```
TapProducer tapProducer = TapProducerFactory.makeTap13Producer();
testSet testSet = new testSet();

// Creating a Plan with 2 test Result's
Plan plan = new Plan( 2 );
testSet.setPlan(plan);

// Creating a test Result with a status ok
testResult tr1 = new testResult( StatusValues.OK, 1 );
testSet.addtestResult(tr1);

// Creating a test Result with status not_ok
testResult tr2 = new testResult( StatusValues.NOT_OK, 2 );
testSet.addtestResult(tr2);

// Retrieving the TAP content and printing it to the default output
String tapStream = tapProducer.dump( testSet );
System.out.println( tapStream );
```

The code above will generate the following TAP output:

```
1..2
ok 1
not ok 2
```

## Reading TAP using a TAP Consumer

If you understood about how tap4j works, reading a TAP Stream will be quite easy for you. You just have to create a TAP Consumer using guess what? Yeah, a [TapConsumerFactory](http://tap4j.sourceforge.net/apidocs/org/tap4j/consumer/TapConsumerFactory.html). The method of the TAP Consumer to load TAP is load(). This method will return a [TestSet](http://tap4j.sourceforge.net/apidocs/org/tap4j/model/TestSet.html). Let's read the output from the previous section.

```
TapConsumer tapConsumer = TapConsumerFactory.makeTap13Consumer();
String tapStream = "1..2\n" +
		"ok 1\n" +
		"not ok 2";
testSet testSet = tapConsumer.load(tapStream);

System.out.println(testSet.getNumberOftestResults());

System.out.println(testSet.gettestResult(2).getStatus());

System.out.println(testSet.containsNotOk());
```
The code above will generate the following output:

```
2
not ok
true
```