# Benchmark CLI


### Wymagania

- Zainstalowana JDK 11 (lub wyższa, testowane było na 11 bo to obecny LTS).
- Należy pamiętać: 
  - o ustawieniu zmiennej środowiskowej `JAVA_HOME` wskazującej
  na katalog gdzie zainstalowaliśmy JDK.
  - oraz updejtowaniu zmiennej środowiskowej `PATH` tak by zawierała w sobie 
    również ścieżkę do `${JAVA_HOME}/bin`
  
- Projekt jest budowany maven'em. Używamy maven-wrappera Proszę zwrócić uwagę że poniżej 
  używamy komendy `mvnw` a nie `mvn`. W związku z tym instalacja lokalna mavena nie jest 
  potrzebna - a wręcz niewskazana (ze względu na ryzyko niezgodności wersji).
  
- Połączenie internetowe - maven ściąga zadeklarowane zależności z internetu 
  podczas pierwszego builda.


### Struktura katalogu

Struktura katalogów wygląda tak:

```
-- .mvn
-- src
   -- main
      -- java
      -- resources
   -- test
      -- java
      -- resources
-- .gitgnore
-- mvnw
-- mvnw.cmd
-- pom.xml
-- README.md
```

- Źródła programu są w podkatalogoach `/src/main`
- Z kolei `/src/test` zawiera źródła unit testów.
- Podkatalog `.mvn` oraz pliki `mvnw` i `mvnw.cmd` to maven-wrapper.
- Plik `pom.xml` to deskryptor projektu i jego zaelżności dla mavena.
  

### Praca z maven'em

Wszystkie komendy poniżej wykonujemy z katalogu głównego projektu 
(czyli tam gdzie jest plik `pom.xml` oraz ten plik - `README.md`).


### 1. Budowanie projektu

Wchodzimy w terminalu do katalogu głównego projektu (czyli tam gdzie jest plik `pom.xml`).
Z lini poleceń wykonujemy:

```
mvnw package -DskipTests
```

Opcja `-DskipTests` wyłącza odpalanie testów. Oczywiście można z niej zrezygnować
ale wtedy build będzie trwał dłużej.


### Uruchamianie programu

Zbudowany artefakt znajduje się w podkatalogu `target` głównego folderu projektu.
Jest to plik: `target/benchmark-cli.jar`

Uruchamiamy go (z głównego folderu projektu):

```
java -jar target/benchmark-cli.jar --help
```

Opcja `--help` wyświetla manual naszego programu.


### Uruchamianie testów

Testy uruchamiamy teź komendą:

```
mvnw test
```

Jak opisane wyżej, testy uruchamiają się też podczas builda (o ile nie użyjemy opcji `-DskipTests`).


### Generowanie Javadoc'a

Javadoc'a generujemy komendą:

```
mvnw javadoc:javadoc
```
Wygenerowany javadoc znajduje się w podkatalogu `target/site` głównego folderu projektu.
Otwieramy plik `target/site/index.html` w przeglądarce.
