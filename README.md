# PHP Developer Coding Exemplar

## Instructions
This coding exemplar is designed to highlight your skills and areas of expertise with the PHP language in general. We rely mainly on PHP as our web technology of choice. Because of this, it's important that developers have a well-rounded understanding of the PHP language.

Please complete the following questions to the best of your ability. If you are unable to solve a question, please indicate as such. You should feel free to use the PHP manual and other resources to solve these questions; after all, we expect that our developers will use their problem-solving skills at work! Some questions are intended to be difficult, while others are meant to be easy or obvious. Please post your answers in a **secret** `Gist`, using `Markdown` format, and send the link for review.

This exercise should take approximately one hour to complete.

Good luck!

## Question 1
You've been tasked with identifying a string that contains the word "superman" (case insensitive). You've written the following code:
```php
<?php

if(!strpos(strtolower($str), 'superman')) {
	throw new Exception;
}
```

QA has come to you and said that this works great for strings like "I love superman", but an exception is generated for strings like "Superman is awesome!", which should not happen. Explain why this occurs, and show how you would solve this issue (you must use strpos() in your answer).

## Question 2
A client has called and said that they're noticing performance problems on their database when searching for a user by email address. You've checked, and the following query is running:

```
SELECT * FROM users WHERE email = 'user@test.com';
```

You run the EXPLAIN command and get the following results:

```
+----+-------------+-------+------+---------------+------+---------+------+-------+-------------+
| id | select_type | table | type | possible_keys | key  | key_len | ref  | rows  | Extra       |
+----+-------------+-------+------+---------------+------+---------+------+-------+-------------+
|  1 | SIMPLE      | users | ALL  | NULL          | NULL | NULL    | NULL | 10320 | Using where |
+----+-------------+-------+------+---------------+------+---------+------+-------+-------------+
```

Offer a theory as to why the performance is slow.

## Question 3
Starting with PHP 5.5, what is the recommended way to hash user passwords? Show some code that illustrates how you would hash a user's password, and also how you would check that a password supplied by a user matches the password on file.

If your client cannot upgrade to PHP 5.5, and you have to hash passwords using existing PHP libraries, what is one library/package that makes this easy?

## Question 4
You're given a sorted index array that contians no keys. The array contains only integers, and your task is to identify whether or not the integer you're looking for is in the array. Write a function that searches for the integer and returns true or false based on whether the integer is present. Describe how you arrived at your solution.

## Question 5
During a large data migration, you get the following error: Fatal error: Allowed memory size of 134217728 bytes exhausted (tried to allocate 54 bytes). You've traced the problem to the following snippet of code:

```php

$stmt = $pdo->prepare('SELECT * FROM largeTable');
$stmt->execute();
$results = $stmt->fetchAll(PDO::FETCH_ASSOC);
foreach ($results as $result) {
	// manipulate the data here
}
```
Refactor this code so that it stops triggering the memory error.

## Question 6
Write a function that takes a phone number in any form and formats it using a delimiter supplied by the developer. The delimiter is optional; if one is not supplied, use a dash (-). Your function should accept a phone number in any format (e.g. 123-456-7890, (123) 456-7890, 1234567890, etc) and format it according to the 3-3-4 US block standard, using the delimiter specified. Assume foreign phone numbers and country codes are out of scope.

*Note:* This question CAN be solved using a regular expression, but one is not REQUIRED as a solution. Focus instead on cleanliness and effectiveness of the code, and take into account phone numbers that may not pass a sanity check.

## Question 7
In production, we'll be caching to memcache. On staging, we'll be caching to APC. In development, we won't be caching at all. Design a library that allows you to store and retrieve data from the cache (only two methods required) and fits the requirements of all three environments. Consider making use of anything appropriate (e.g. traits, classes, interfaces, abstract classes, closures, etc) to solve this problem.

Note: This is an architecture question. Please focus on the design of your library, rather than implementation or the specific caches I've described.

## Question 8
Write a complete set of unit tests for the following code:

```php

function fizzBuzz($start = 1, $stop = 100)
{
	$string = '';
	
	if($stop < $start || $start < 0 || $stop < 0) {
		throw new InvalidArgumentException;
	}
	
	for($i = $start; $i <= $stop; $i++) {
		if($i % 3 == 0 && $i % 5 == 0) {
			$string .= 'FizzBuzz';
			continue;
		}
		
		if($i % 3 == 0) {
			$string .= 'Fizz';
			continue;
		}
		
		if ($i % 5 == 0) {
			$string .= 'Buzz';
			continue;
		}
		
		$string .= $i;
	}
	
	return $string;
}
```

## Question 9
I've developed a class called Select to represent the SELECT statements I'd normally write for a database. I want to be able to use the Select objects as queries and automatically cast them to strings, but when I use them in PDOStatement::execute() I get the following error: Catchable fatal error: Object of class Select could not be converted to string. What should I change in my Select class so that this error goes away?

## Question 10
I have an array of file names:

```php
$files = [
	'/usr/share/nginx/wordpress/wp-content/themes/index.php',
	'/usr/share/nginx/wordpress/wp-content/themes/mytheme.php',
	'/usr/share/nginx/wordpress/wp-content/plugins/myplugin.php',
	'/usr/share/nginx/wordpress/wp-content/plugins/akismet.php',
	'/usr/share/nginx/wordpress/wp-content/uploads/november.jpg',
];
```

Below is a mixed list of specific file names, as well as file paths, that should be excluded. For example, ALL files under a file path should be excluded, but if the value is an actual file name, only that specific file should be excluded. 

```php
$exclude = [
	'/usr/share/nginx/wordpress/wp-content/uploads',
	'/usr/share/nginx/wordpress/wp-content/plugins/myplugin.php',
];
```

For example, you'll want to exclude the uploads directory (and all files in it), but ONLY the myplugin.php file.

Devise a method for applying the exclusion list against the file list WITHOUT nested foreach() loops.
