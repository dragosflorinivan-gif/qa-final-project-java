Badge status


[![CI Pipeline for QA Project](https://github.com/dragosflorinivan-gif/qa-final-project-java/actions/workflows/ci.yaml/badge.svg)](https://github.com/dragosflorinivan-gif/qa-final-project-java/actions/workflows/ci.yaml)

SCOPE

Verificarea unui endpoint al unui API folosind un pipeline configurat si Docker

EXECUTARE

Local, folosim comanda *mvn test* (Java si Maven preinstalate). 
Tips&tricks: Maven nu are executabil de instalare -> descarci zip si extragi datele -> configurezi variabilele de mediu -> rulezi in cmd mvn -version 
target/maven-status/maven-compiler-plugin/testCompile/default-testCompile


Folosind Docker si pipeline configurat in App.yaml (\config), executand urmatorii pasi:

Construieste imaginea Docker:
*docker build -t qa-project-java .*

Ruleaza testele
*docker run --rm qa-project-java*

Publicarea testelor:
  1. Autentificarea
  *docker login*
  2. Etichetarea
  *docker tag qa-project-java <your-username>/qa-project-java:1.0*
  3. Publicarea
  *docker push <your-username>/qa-project-java:1.0*

Acum testele sunt live si pot fi rulate cu urmatoarea comanda:
*docker run --rm <your-username>/qa-project-java:1.0*

e.g. *docker run --rm dragosflorinivan/qa-project-java:1.0*

INTEGRARE CI/CD

De fiecare data cand se face push pe branch-ul principal, se ruleaza automat teste (vizibile in Git->Actions).
Acest lucru este posibil cu ci.yaml (.github\workflows)