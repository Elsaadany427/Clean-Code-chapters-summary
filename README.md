# Clean-Code-chapters-summary
 summary about clean code book 

# 

# Chapter 2: Meaningful Names

## 

## 1. Use Intention-Revealing Names

### 

### Ex 1:

```
int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDays;
```

### Ex 2:

Before:

```
public List<int[]> getThem() {
    List<int[]> list1 = new ArrayList<int[]>();
    for (int[] x : theList)
        if (x[0] == 4)
            list1.add(x);
    return list1;
}
```

After:

```
public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard)
        if (cell[STATUS_VALUE] == FLAGGED)
            flaggedCells.add(cell);
    return flaggedCells;
}
```

## 2. Avoid disinformation

- Avoid leaving false clue that obscure the meaning of code: `hp`, `aix`, `sco`.
- Avoid use lower-case `L` or upper-case `o` as variable names.

## 3. Make meaningful Distinctions

- Number-serires naming `(a1, a2,..., aN)` are non-informative
- Noise words are meaningless distinction: `ProductInfo`, `ProductData`
- `variable` should never appear in a variable name
- `table` should never appear in a table name
- `Name` is alway better than `NameString`

## 4. Use pronounceable names

Before:

```
class DtaRcrd102 {
    private Date genymdhms;
    private Date modymdhms;
    private final String pszqint = "102";
    /* ... */
};
```

After:

```
class Customer {
    private Date generationTimestamp;
    private Date modificationTimestamp;;
    private final String recordId = "102";
/* ... */
};
```

## 5. Use searchable names

- Single-letter names can ONLY used as local variables.
- The length of a name should correspond to the size of its scope.

Before:

```
for (int j = 0; j < 34; j++){
    s += (t[j] * 4) / 5;
}
```

After:

```
int realDaysPerIdealday = 4;
const int WORK_DAYS_PER_WEEK = 5;
int sum = 0;
for (int j = 0; j < NUMBER_OF_TASKS; j++){
    int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
    int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
    sum += realTaskWeeks;
}
```

## 6. Avoid Encodings

### Member Prefixes

From this

```
public class Part {
    private String m_dsc; // The textual description
    void setName(String name) {
        m_dsc = name;
    }
}
```

To:

```
public class Part {
    String description;
    void setDescription(String description) {
        this.description = description;
    }
}
```

### 

### Interfaces and Implementations

We must encode either interface or the implementation. Ex: `IShapeFactory`, `ShapeFactory` or `ShapeFactory`, `ShapeFactoryImp`

## 

## 7. Avoid mental mapping

- Use single-letter variable names for a loop counter if its scope is very small

## 

## 8. Class names

- Should have noun or noun pharse names. Ex: `Customer`, `WikiPage`, `Account`.
- Avoid words like: `Manager`, `Processor`, `Data`, `Info`.
- Should not be a verb.

## 9. Method names

- Should have verb or verb pharse name. Ex: `postPayment`, `deletePage`, `save`.
- Accessors, mutators, predicates should be named for their value, prefixed with `get`, `set`, `is`.

```
String name = employee.getName();
customer.setName("mike");
if (paycheck.isPosted())...
```

## 10. Don't be cute

Will they know what the function named HolyHandGrenade is supposed to do? Sure, it’s cute, but maybe in this case
DeleteItems might be a better name.

## 11. Pick one word per concept

## 

## 12. Don't pun

## 

## 13. Use solution domain names

## 

## 14. Use problem domain names

- Use the name from problem domain when there is no "programmer-eese" for what we're doing.

## 

## 15. Add meaningful context

```
Variables have a context.
public class GuessStatisticsMessage {
	private String number;
	private String verb;
	private String pluralModifier;
	public String make(char candidate, int count) {
	createPluralDependentMessageParts(count);
	return String.format(
	"There %s %s %s%s",
	verb, number, candidate, pluralModifier );
}
private void createPluralDependentMessageParts(int count) {
	if (count == 0) {
		thereAreNoLetters();
	} else if (count == 1) {
		thereIsOneLetter();
	} else {
		thereAreManyLetters(count);
	}
}
private void thereAreManyLetters(int count) {
	number = Integer.toString(count);
	verb = "are";
	pluralModifier = "s";
}
private void thereIsOneLetter() {
	number = "1";
	verb = "is";
	pluralModifier = "";
}
private void thereAreNoLetters() {
	number = "no";
	verb = "are";
	pluralModifier = "s";
	}
}
```

## 16. Don't add gratutious context

Variables with unclear context.

```
`private void printGuessStatistics(char candidate, int count) {`
	`String number;`
	`String verb;`
	`String pluralModifier;`
	`if (count == 0) {`
		`number = "no";`
		`verb = "are";`
		`pluralModifier = "s";`
	`} else if (count == 1) {`
		`number = "1";`
		`verb = "is";`
		`pluralModifier = "";`
	`} else {`
		`number = Integer.toString(count);`
		`verb = "are";`
		`pluralModifier = "s";`
	`}`
	`String guessMessage = String.format(`
	`"There %s %s %s%s", verb, number, candidate, pluralModifier`
	);
	print(guessMessage);
}
```



## 17. Final words

- Choosing good names requires good descriptive skills and a shared cultural background



# 

# Chapter 3: Functions

## 1. Small

- Function should be small
- *They should be smaller than that*
- Function should hardly ever be 20 lines long.

## 2. Do one thing

- *FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.*

## 3. One level of abstraction per function

## 4. Switch statements

- Bury the `switch` statement in the basement of an ABSTRACT FACTORY
- Create polymorphic objects, hidden behind an inheritance relationship

## 5. Use descriptive names

- Don't be afraid to make a name long.
- Don't be afraid to spend time choosing a name.
- Use the same phrases, nouns, and verbs in the function name

## 6. Function Arguments

- The ideal number of arguments for a function is
  zero (niladic). Next comes one (monadic), followed
  closely by two (dyadic).

- Three arguments (triadic) should be avoided where possible

- Using an output argument instead of a return value for a transformation is confusing.

- Flag arguments are ugly => Split the function into two

  

## 7. Have no side effects

## 8. Command Query Separation

Functions should either do something or answer something, but not both.

## 9. Prefer Exceptions to Returning Error codes

Turn this

```
if (deletePage(page) == E_OK) {
    if (registry.deleteReference(page.name) == E_OK) {
        if (configKeys.deleteKey(page.name.makeKey()) == E_OK){
            logger.log("page deleted");
        } else {
            logger.log("configKey not deleted");
        }
    } else {
    logger.log("deleteReference from registry failed");
    }
} else {
    logger.log("delete failed");
    return E_ERROR;
}
```

to this

```
try {
    deletePage(page);
    registry.deleteReference(page.name);
    configKeys.deleteKey(page.name.makeKey());
} 
catch (Exception e) {
    logger.log(e.getMessage());
}
```

## 10. Don't Repeat Yourself

Duplication may be the root of all evil in software

## 

## 11. Structured Programming

Dijkstra said that every function, and every block within a function, should have one entry and one exit

It mean that there should only be one return statement in a function, no `break` or `continue` statements in a loop, and never, *ever*, any `goto` statements.
