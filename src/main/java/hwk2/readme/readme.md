Using count,Number of Cities in the USA:

mysql> SELECT COUNT(*) FROM city WHERE CountryCode = 'USA';

Find out Population and Average Life Expectancy in Argentina (ARG):

mysql> SELECT Population, LifeExpectancy FROM country WHERE Code = 'ARG';

Display Cities for a Country (e.g., Brazil):

mysql> SELECT Name FROM city WHERE CountryCode = 'BRA';

Two Additional Queries (e.g., Highest Population and Lowest Life Expectancy):

mysql> SELECT Name, Population FROM country ORDER BY Population DESC LIMIT 1;
mysql> SELECT Name, LifeExpectancy FROM country WHERE LifeExpectancy IS NOT NULL ORDER BY LifeExpectancy ASC LIMIT 1;