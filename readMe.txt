/***************************
Jane Kim jk3316
HW 5 Programming
FactbookReader program
readMe.txt
/***************************

HOW TO EXECUTE:
Please run this program with a larger allocated amount of space for the Java Heap space. 
In Eclipse, run with VM argument: -Xmx2000m
Configure Answer class to change parameters for searching for answers

FactbookAnalyzer
Tester class that contains the main method
contains URLGetter and Answer (answers questions)

Country
when initialized, has name and initials that are in the URL
has variables for each category of information
has getters and setters that convert Strings into information that Answer can use
has number converting methods (convertInt and convertDouble)
has itemCount that counts items in a string list
has compareTo method that compares countries based on electricity consumption per capita
has printInfo() which is like a toString(); prints all the parsed information about the country

URLGetter
creates a connection to the CIA World Factbook
gets a list of countries from the main page
navigates to each country's page and parses relevant information
uses Jsoup to navigate "elements" of the HTML in a Document to find relevant information
has a method to print the status code, ensuring the connection was established
getCountries()
ignores items from the main page that are not countries (e.g. oceans)
catches necessary exceptions, especially OutOfMemory which lets the user know if the program needs more heap space to execute
parseFacts()
gets all the information by searching all the elements for relevant text

Answer
constructor asks each question
MODIFY THIS CLASS TO CONFIGURE THE QUESTIONS YOU WANT TO ANSWER
getAnswer1 looks for all countries in the specified continent then searches for all instances of the natural hazard
getAnswer2 compares elevation points and returns the one with the lowest
getAnswer3 searches the geographic coordinates for directions, this one searches for 'S' and 'E'.
getAnswer4 gets all countries with more than 10 political parties
getAnswer5 searches flag description for the specified colors
etc, etc
most of the getAnswer methods adds the countries that fulfill the constraints into a list of  results for that specific question and prints the country's name in the console



WORKSPACE - my work process
lists the relevant information to be parsed for each question
Asia: containing Asia, Middle EAst

1. List countries in South America that are prone to earthquakes.
Map references, Natural hazards
configurable: continent, kind of natural hazard
 
2. Find the country with the lowest elevation point in Europe.
Map references, [lowest] Elevation extremes
config: continent

3. List all countries in the southeastern hemisphere.
Geographic coordinates
config: hemisphere

4. List countries in Asia with more than 10 political parties.
Map references, Political parties and leaders
config: continent, # of political parties

5. Find all countries that have the color blue in their flag.
Flag description
config: color

X 6. Find the top 5 countries with the highest electricity consumption per capita. (Electricity
consumption % population)
Electricity - consumption % Population
config: number of top countries

7. entirely landlocked by a single country. Find these countries.
[0km] Coastline, [Border countries: only one] Land boundaries
config: none

X 8. I want to go on a vacation with a friend. Our goal is to visit as many capital cities as we can in as
short a geographical distance as possible. To make things easier (and not worry about spherical geometry), 
we are fine with traveling to capitals that are within 10 degrees of latitude and longitude of each other. 
Find the lat/long coordinates and the list of countries/capitals so that the number of capitals is maximized.
Geographic coordinates, Capital
config: degrees

9. Find the country with the highest percentage of people in the agricultural sector in Europe
Map references, Labor force - by occupation
config: continent

10. Find all the countries in Asia that speak more than 2 languages.
Map references, Languages
config: continent