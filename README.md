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
## Action lines
These are very basic, you can describe an event or action in plain text using character abbreviations if applicable.
```
A goes to the loo;
M finds a peach cobbler on the floor;
Qn wins RuPaul's Drag Race Season 28;
```
They all must end in a semicolon if they are individual.

## `details {*show_details*}`
It is recommended  to include a dictionary named `details` with information about the show. They will usually include `show`,  `episode`, `season`, and `name`, but this is not required.

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
*(To avoid confusion, **Char** will refer to a single symbol character, and **Character** will refer to a show character.)*

In order to save up on space, a `chars` dictionary should be included to abbreviate the names of any characters in the show.

Commonly an uppercase char (e.g. A, Q) is used to denote main characters,  but there may be a few issues with this (see below).
### Naming issues
#### Overlap
In the case of the characters sharing a char, another lowercase inital may be used.
```
chars {
	Sc: Sonic the Hedgehog;
	Sq: Sonique Hart;
	
	Sfm: Sheriff Mao Mao;
	Spm: Super Mario;
}
```
*Please note that although this is to save space, abbreviations should still be readable.
As such, abbreviating* `Sherrif Mao Mao` *to* `Sh` *would be a little unfavourable compared to* `Sfm`.

#### Unknown Characters
When encountering characters who do not have a name, or are not well known enough in the scope of the episode, they should be represented by `Ch0`, `Ch1`, `Ch2` etc., along with a description of their role.
```
chars {
	F: foo;
	B:
```
## `location (*details*) {*actions*}`
