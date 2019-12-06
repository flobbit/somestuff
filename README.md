# NP Calculation

## Single Loss

### Criteria for packaging
BlaBla

|Field|
|:---|
|LossId|
|ContractId|
|CoverId|
|OccurrencePeriodStart|
|OccurrencePeriodEnd|
|UnderwritingPeriodStart|
|UnderwritingPeriodEnd|

### Criteria for Current State Selection
Following fields of existing Gross Postings have to be selected.

|Field|
|:---|
|EntryCode|
|LossId|
|Cedent|
|ClassOfBusiness|
|TypeOfBusiness|
|UnderwritingArea|
|LineOfBusiness|
|AsOf|
|CurrencyTranslationDate|
|OccurrencePeriodStart|
|OccurrencePeriodEnd|
|UnderwritingDate|
|ContractId|
|RiskId|
|CoverId|
|Amount|
|Currency|

### Criteria for Sorting within a functional package
The existing Gross Postings and the newly delivered Gross Postings have to be sorted to avoid unnecessary re-bookings 
and to ensure that the calculation is replicable. 

|Sort Order|Field|
|:---|:---|
|1|EntryCode (from Amounts Covered)|
|2|Cedent|
|3|ClassOfBusiness|
|4|TypeOfBusiness|
|5|UnderWritingArea|
|6|LineOfBusiness|
|7|AsOf|
|8|CurrencyTranslationDate|

```puml
@startuml
skinparam shadowing false
skinparam componentStyle uml2
skinparam linetype ortho
actor Foo1
boundary Foo2
control Foo3
entity Foo4
database Foo5
collections Foo6
Foo1 -> Foo2 : To boundary
Foo1 -> Foo3 : To control
Foo1 -> Foo4 : To entity
Foo1 -> Foo5 : To database
Foo1 -> Foo6 : To collections
@enduml
```

```puml
@startuml
skinparam shadowing false
skinparam componentStyle uml2
skinparam linetype polyline

scale 600 width

[*] -> State1
State1 --> State2 : Succeeded
State1 --> [*] : Aborted
State2 --> State3 : Succeeded
State2 --> [*] : Aborted

note left of State2: Servus

state State3 {
  state "Accumulate Enough Data\nLong State Name" as long1
  long1 : Just a test
  [*] --> long1
  long1 --> long1 : New Data
  long1 --> ProcessData : Enough Data
}
State3 --> State3 : Failed
State3 --> [*] : Succeeded / Save Result
State3 --> [*] : Aborted
 
@enduml
```
