# The Essence of Showfiles
A showfile is a code-based way to describe the events that happen in various forms of visual media, particularly TV shows.
The code is loosely based off of C / Java in terms of `keyword (argument) {function;}` syntax, as well as others like `[lists]` and `{key-value: dictionaries}`. 

*Please note, however, that unlike many programming languages, strings do not require to be contained in quotes although you may decide to do this for aesthetic purposes.*

### Example
``` 
details {
	show: As the Wind Blows;
	season: 3;
	episode: 11;
	name: Rose Petals;
}

chars {
	A: Annabel;
	B: Benjamin;
}

START

LIVING_ROOM (constantly panning) {
	A sits on the floor eating cookies and watching TV;
	B comes in and comments on the lack of cleanliness;
	A doesn't respond and continues to eat;
	sim {
		
		voiceover {
			A talks about lack of motivation;
			A constantly gets distracted while doing so;
		},
		
		flash (back) {
			A sitting in bedroom focusing on a robin;
			The robin disappears but A does not react; 
	}
}

END
```


# Basic syntax

## `;`

As with most other non-whitespace based languages, a semicolon is used at the end of lines that are not wholly surrounded by brackets.
```
SOME_LOCATION {
	This is a single line;
	This is another single line;
	Since these are individual lines;
	They must be closed with semi-colons;
	
	This is inside a location function;
	Since there are brackets at the beginning and end;
	A semi-colon is not required after the closing bracket; 
}
```
Originally the semicolons were originally commas, but commas in the middle of action lines would divide them into two.



## `details {*show_details*}`

A dictionary that outlines details of the episode.

It is recommended to include `show`,  `episode`, `season`, and `name`, but this is not required.

*Please note that dates can be arranged in any order given that day, month, and year should be prefaced with D, M, and Y respectively.*
```
details {
	show: Chowder;
	season: 4;
	episode: 4;
	name: The Spookiest House in Marzipan;
	// extra terms that can be included
	synopsys: Gazpacho tells a story about Chowder having to deliver an order to a scary house.;
	first_aired: D22M10Y2009
} 
```
## `chars {*char_details*}`

A  dictionary to abbreviate the names of any characters in the show.

*(To avoid confusion, **Char** will refer to a single symbol character, and **Character** will refer to a show character.)*

The uppercase initial should be used to denote the characters's names where possible:
`S: Sandy Cheeks; H: Haru ; O: Olaf; W: Winnie the Pooh`
However, there may be a few issues with this (see below).
### Naming issues
#### Overlap
When two characters share the same initial, another lowercase char may be added, or an alternative char may be used. 
```
// Adding another character
chars {
	Sc: Sonic (the Hedgehog);
	Sq: Sonique (Hart);
	Shfm: Sheriff Mao Mao;
	Spm: Super Mario;
}
```
*Please note that although saving space is optimal, abbreviations should still be readable.
As such, abbreviating* `Sherrif Mao Mao` *to* `Sh` *would be unfavorable compared to* `Shfm`.
```
// Using alternative letter
chars {
	K: King;
	N: Knight;
}
```

#### Unknown Characters
When encountering characters significant to the plot, but do not have a name or are not well known enough in the scope of the episode, they should be represented by `Ch0`, `Ch1`, `Ch2` etc., along with a description of their role.
```
chars {
	F: Foo;
	Br: Bar;
	Bz: Baz;

	Ch0: Fox who follows Br;
	Ch1: Person behind F in hospital line;
	Ch2: Friend of Ch1;
}
```
Preferably they should be in order of appearance for readability but this is not necessary.
## Action lines
These are very basic, you can describe an event or action in plain text using character abbreviations if / where applicable.
When referring to two or more characters, put all of the abbreviated chars together.
```
A goes to the loo;
M finds a peach cobbler on the floor;
GDw put on aluminium hats;
```
*Please note that `GDw` refers to characters `G` and `Dw`. The addition of new lowercase chars referring to one character still applies with this rule.*

## `location (*details*) {*actions*}`
A function that describes the current location of the scene.

Where applicable, any extra details about the scene should be placed inside the `(details)` brackets separated by commas.

```
PARK (panning as AB run) {
	A is sweating and chasing after B;
	B taunts A;
	AB continue to run across the park;
}
```

```
SCHOOL_HALLWAY (in front of lockers, day, 14:00) {
	G criticises D for being manipulative;
	D criticises G for being a pushover;
	GD continue to bicker;
}
```
## `voiceover (*details*) {*actions*}`
Simple function to describe a voiceover or narration.
```
voiceover {
	N talks to B about carrots;
}
```
