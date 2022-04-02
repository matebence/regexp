# Description

- Regular Expressions are symbols representing a text pattern
- Its a formal language interpreted by a regular expression processor
- Used for matching, searching and replacing text


# History

- 1943 Wareb NcCulloch and Walter Pitts develop model of how the nervous system works
- 1956 Stephen Kleene describes these models with an algebra called "regular sets"
- 1968 Ken Thompson implement regex in ed(an early Unix text engine)
- 1986 POSIX - Standard to ensure compatiblity
	- Two type of implementations
		- Basic Regular Expressions (legacy tools)
		- Extended Regular Expressions (modern tools)
- 1986 Henry Spencer releases a regex library written in C
- 1987 Larry Wall releases Perl


# Regex engines

- C/C++
- Java
- JavaScript/ActionSscript(ECMAScript)
- .NET
- Perl
- PHP
- Python
- Ruby
- Unix
- Apache
- MySQL


## Notation

[Test environment](https://www.regexpal.com/)

`
/yourRegex/
`

|Modes 			 |Syntax 		|
|----------------|--------------|
|Standard 		 |`/yourRegex/` |
|Global  		 |`/yourRegex/g`|
|Case-insenstive |`/yourRegex/i`|
|Multiline 		 |`/yourRegex/m`|
|Dot-matches-all |`/yourRegex/s`|


## Metacharacters

` - \ . * + - {} [] ^ $ | ? () : ! = `

Characters with special meaning.


## Matching literator characters

Case sensitive by default.

`
/car/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`car` 		 					   		   |🟢			  |**car** 		 					   |
|`CAR` 		 					   		   |🔴			  |CAR 	 		 					   |
|`carnival`  		 					   |🟢			  |**car**nival 				       |

## Wildcards

|Symbol 			 |Description 				  |
|--------------------|----------------------------|
|. 		 		 	 |Any character except newline|

Matches any one character except new line.

`
/h.t/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`hot` 		 					   		   |🟢			  |**hot** 		 					   |
|`hat` 		 					   		   |🟢			  |**hat** 	 		 				   |
|`hitting`  		 					   |🟢			  |**hit**ting 					       |
|`heat`  		 					   	   |🔴			  |heat 				       		   |

## Escaping

|Symbol 			 |Description 				  |
|--------------------|----------------------------|
|\ 		 		 	 |Escape the next character   |

Allows use of metacharacters as literal characters.

`
/h.._export\.txt/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`his_export.txt` 				   		   |🟢			  |**his_export** 		 			   |
|`her_export.txt` 				   		   |🟢			  |**her_export.txt** 	 			   |

## Special characters

|Symbol 			 |Description 				  	|
|--------------------|------------------------------|
|  		 		 	 |Space   						|
|\t  			 	 |Tab    						|
|\r  	 		 	 |Line return (depend on OS)    |
|\n  	 		 	 |Line return (depend on OS)    |
|\r\n  	 		 	 |Line returns (depend on OS)   |

`
/c a t/g
/a\tb/g
/c\nd/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`c a t` 				   		   		   |🟢			  |**c a t** 		 				   |
|`a 	b` 				   				   |🟢			  |**a 	b** 	 			   		   |


## Defining a character set

|Symbol 			 |Description 				  |
|--------------------|----------------------------|
|[ 		 		 	 |Beging character set 		  |
|] 		 		 	 |End of character set        |

Any one of several characters, but only one character. Order of characters doesnt matter.

`
/c[aeiouw]t/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`cat` 		 					   		   |🟢			  |**cat** 		 					   |
|`camel` 		 					   	   |🔴			  |camel 		 					   |
|`cow`  		 					   	   |🔴			  |cow				       			   |

## Character range

|Symbol 			 |Description 				  |
|--------------------|----------------------------|
|\- 		 	 	 |Range of characters 		  |

Matches all characters between two specified character. Any one of several characters, but only one character.

`
/[0-9][0-9][0-9]-[0-9][0-9][0-9]-[0-9][0-9][0-9]/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`555-666-777` 		 					   |🟢			  |**555-666-777** 		 			   |
|`aaa-bbb-ccc` 		 					   |🔴			  |aaa-bbb-ccc 		 			  	   |

## Negative character sets

|Symbol 			 |Description 				  |
|--------------------|----------------------------|
|^ 		 		 	 |Negate a character set 	  |

Not any one of several characters.

`
/[^a-zA-Z ]/g
`

|Test String 			 				   			 |Is matching?  |How? 					 							    |
|----------------------------------------------------|--------------|-------------------------------------------------------|
|`Now we known how to made negative character sets.` |🟢			  	|Now we known how to made negative character sets**\.** |

## Metacharacters inside character sets

Metacharacters inside character sets are already escaped. Do not need to escape them again. Exeptions are ] - ^ \

## Shorthand characters sets

|Shordhand 		 |Meaning 			  |Equivalent  		|
|----------------|--------------------|-----------------|
|\d   			 |Digit   			  |[0-9]  		    |
|\w 			 |Word character 	  |[a-zA-z0-9_]	  	|
|\s 			 |Whitespace 		  |[ \t\r\n]   		|
|\D 			 |Not digit 		  |[^0-9] 			|
|\W 			 |Not word character   |[^a-zA-Z-0-9_]	|	
|\S 			 |Not White space 	  |[^ \t\r\n] 	    |

## POSIX Bracket expressions

|Shordhand 		 |Meaning 			   				  |
|----------------|------------------------------------|
|[:alpha:] 		 |Alphabetic characters  		      |
|[:digit:] 		 |Numeric characters  		          |
|[:alnum:] 		 |Alphanumeric characters  		      |
|[:lower:] 		 |Lowercase alphabetic characters  	  |
|[:upper:] 		 |Uppercase alphabetic characters  	  |
|[:punct:] 		 |Punction characters  		      	  |
|[:space:] 		 |Space characters  		      	  |
|[:blank:] 		 |Blank characters  		      	  |
|[:print:] 		 |Printable characters, spaces  	  |
|[:graph:] 		 |Printable characters, no spaces  	  |
|[:cntrl:]		 |Control characters (non printable)  |
|[:xdigit:] 	 |Hexidecimal characters  		      |


## Repetation meta character

|Symbol 			 |Description 				       |
|--------------------|---------------------------------|
|* 					 |Preceding item zero or more time |
|+ 				 	 |Preceding item one or more times |
|? 					 |Preceding item zero or one time  |


`
/apples*/g 
`

|Test String 	|Is matching?   |How? 					 	|
|---------------|---------------|---------------------------|
|`apple`  		|🟢			  	|**apple**  				|
|`apples`  		|🟢			  	|**apples** 				|
|`applesssssss` |🟢			  	|**applesssssss** 			|

`
/apples+/g
`

|Test String 	|Is matching?   |How? 					 	|
|---------------|---------------|---------------------------|
|`apple`  		|🔴			  	|apple 		 				|
|`apples`  		|🟢			  	|**apples** 				|
|`applesssssss` |🟢			  	|**applesssssss** 			|

`
/apples?/g
`

|Test String 	|Is matching?   |How? 					 	|
|---------------|---------------|---------------------------|
|`apple`  		|🟢			  	|**apple**  				|
|`apples`  		|🟢			  	|**apples** 				|
|`applesssssss` |🔴			  	|applesssssss 				|

## Quantified repetition

|Symbol 		 |Description 				  					   |
|----------------|-------------------------------------------------|
|{ 		 	 	 |Start quantified repetition of preceding item    |
|} 		 	 	 |End quantified repetition or preceding item 	   |

- {min, max} this is the basic syntax
- min and max are positive numbers
- min must always be included, can be zero
- max is optional

- \d{4,8} matches numbers with four to eight digits
- \d{4} matches numbers with exactly four digits (min is max)
- \d{4,} matches numbers with four or more digits (max is infinitive)

`
/\d{3}-\d{3}-\d{4}/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`555-687-5309` 		 				   |🟢			  |**555-687-5309** 		 		   |
|`555-687-530966` 		 				   |🟢			  |**555-687-5309**66	 			   |
|`aaa-bbb-cccccc` 		 				   |🔴			  |aaa-bbb-ccc 		 			  	   |

`
\w+_\d{2,4}-\d{2}
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`report_1997-04` 		 				   |🟢			  |**report_1997-04** 		 		   |
|`budget_03-04` 		 				   |🟢			  |**budget_03-04**		 			   |
|`memo_712539-100` 		 				   |🔴			  |memo_712539-100	 			  	   |

## Greedy vs Lazy (it has only performance impact)

- Greedy strategy
	- Match as much as possible before giving control to the next expression part

- Lazy strategy
	- Match as little as posssible before giving control to the next expression part

|Symbol 		 |Description 				  					   |
|----------------|-------------------------------------------------|
|? 		 	 	 |Make preceding quantifier lazy    			   |

`
\w*?\d{3}
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`vw_golf_022` 		 					   |🟢			  |**vw_golf_022** 		 			   |


## Grouping

|Symbol 			 |Description 				  |
|--------------------|----------------------------|
|( 		 	 	 	 |Start gouped expression 	  |
|) 		 	 	 	 |End grouped expression 	  |

Group portions of the expression.

`
/(abc)+/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`abc` 		 					   		   |🟢			  |**abc** 		 			  		   |
|`abcabcabc` 		 					   |🟢			  |**abcabcabc** 		 			   |

`
/(in)?dependent/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`independent` 		 					   |🟢			  |**independent** 		 			   |
|`dependent` 		 					   |🟢			  |**dependent**	 			  	   |

## Alternation

|Symbol 			 |Description 						  |
|--------------------|------------------------------------|
|\|		 		 	 |Match previous or next expression   |

It represents the logical OR operator. Ordered leftmost expression get precedence.

`
/(peanut|peanutbutter)/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`peanut` 		 					   	   |🟢			  |**cat** 		 					   |
|`peanutbutter` 		 			   	   |🟢			  |**peanut**butter 		 		   |

`
/apple|orange/g
`

|Test String 			 				   |Is matching?  |How? 							   |
|------------------------------------------|--------------|------------------------------------|
|`apple` 		 					   	   |🟢			  |**apple** 		 				   |
|`orange` 		 			   	   		   |🟢			  |**orange** 		 		   		   |

## Repeat and nest

First matched alternation does not effect the next matches

`
(AA|BB|CC){6}
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`AABBAACCAABB` 		 				   |🟢			  |**AABBAACCAABB** 		 				|
|`AABBCCAABBCCAABBCCAABBCCAABBCCAABBCC`    |🟢			  |**AABBCCAABBCCAABBCCAABBCCAABBCCAABBCC** |
|`AAAAAAAAAAAABBBBBBBBBBBBCCCCCCCCCCCC`    |🟢			  |**AAAAAAAAAAAABBBBBBBBBBBBCCCCCCCCCCCC** |
|`ABCABCABCABCCABCABCABCABABBABBABBABB`    |🔴			  |ABCABCABCABCCABCABCABCABABBABBABBABB		|


## Startendanchor

|Symbol 			 |Description 				       |
|--------------------|---------------------------------|
|^ 					 |Start of String / line  		   |
|$ 				 	 |End of String / line   		   |

`
/[a-z ]+$/g 
`

- Without new line

milk\
apple juice\
sweet peas\
yogurt\
sweet corn\
apple source\
milkshake\
**sweet potatoes**


- With new line

milk\
apple juice\
sweet peas\
yogurt\
sweet corn\
apple source\
milkshake\
sweet potatoes\
\n


## Multiline mode

`
/[a-z ]+$/gm
`

- Without new line

**milk**\
**apple juice**\
**sweet peas**\
**yogurt**\
**sweet corn**\
**apple source**\
**milkshake**\
**sweet potatoes**


- With new line

**milk**\
**apple juice**\
**sweet peas**\
**yogurt**\
**sweet corn**
**apple source**\
**milkshake**\
**sweet potatoes**\
\n


## Wordboundaries

|Symbol 			 |Description 				       |
|--------------------|---------------------------------|
|\b 			     |Word boundary (start/end of word)|
|\B				 	 |Not a word boundary  			   |

`
\B\w+\B
`

S**hal**l I c**ompar**e t**he**e to a s**umme**r’s d**a**y?

`
\b\w+\b
`

**Shall** **I** **compare** **thee** **to** **a** **summer**’**s** **day**?


## Backreferences

Grouped expressions are captured. They are accessible via \1 - \9

`
/(apples) to \1/g
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`apple to apple` 		 				   |🟢			  |**apple to apple** 		 				|

## Non capturing

|Symbol 			 |Description 				       |
|--------------------|---------------------------------|
|?: 			     |Specify a non capturing group    |

`
(?:oranges) and (apples) to \1
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`oranges and apples to apples` 		   |🟢			  |**oranges and apples to apples**		    |
|`oranges and apples to oranges` 		   |🔴			  |oranges and apples to oranges		 	|


## Positive lookahead assetions

|Symbol 			 |Description 				       |
|--------------------|---------------------------------|
|?= 			     |Positve lookahead assertion      |

Assertion of what ought to be ahead. If lookahead expression fails, the match fails.

`
(?=seashore)sea
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`seashore` 		  					   |🟢			  |**sea**shore		    					|
|`seaside` 		   					  	   |🔴			  |seaside		 							|

## Negative lookahead assetions

|Symbol 			 |Description 				       |
|--------------------|---------------------------------|
|?! 			     |Negative lookahead assertion     |

Assertion of what not ought to be ahead. If lookahead expression fails, the match fails.

`
(?!seashore)sea
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`seashore` 		   					   |🔴			  |seashore		    			 		    |
|`seaside` 		  						   |🟢			  |**sea**side		 						|


## Matching unicode characters in regex

|Symbol 			 |Description 				       					  |
|--------------------|----------------------------------------------------|
|\u 			     |Unicode indicator     							  |
|\X 			     |Unicode wildcard (matches any single character)     |
|\p{property}	     |Unicode property     								  |
|\P{property}	     |Not unicode property     							  |

|Unicode property 	 |Abbreviation  |
|--------------------|--------------|
|Letter 			 |L 		    |
|Mark 				 |M 			|
|Separator 			 |Z			    |
|Symbol 			 |S 			|
|Number 			 |N 			|
|Punctuation 		 |P		 		|
|Other 				 |C 			|

`
/caf\u00E9/g
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`café` 		  						   |🟢			  |**café**			 						|

`
/caf\X/g
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`café` 		  						   |🟢			  |**café**			 						|

`
/caf\p{L}/g
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`café` 		  						   |🟢			  |**café**			 						|

`
/caf\P{L}/g
`

|Test String 			 				   |Is matching?  |How? 							   		|
|------------------------------------------|--------------|-----------------------------------------|
|`café` 		  						   |🔴			  |café			 							|