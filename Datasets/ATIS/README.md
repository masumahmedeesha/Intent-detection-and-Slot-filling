[中文版本的 README](README.md)
------------------------------

# The ATIS (Airline Travel Information System) Dataset
This repository contains ATIS Dataset in Python pickle format and Rasa NLU JSON format ([https://rasa.com/docs/nlu/dataformat/#json-format](https://rasa.com/docs/nlu/dataformat/#json-format)), also this project provide codes to show how extract data from pickle file.

## Data Sample
### Raw format
```text
   0:         flight: BOS i want to fly from boston at 838 am and arrive in denver at 1110 in the morning EOS
                              BOS                                        O
                                i                                        O
                             want                                        O
                               to                                        O
                              fly                                        O
                             from                                        O
                           boston                      B-fromloc.city_name
                               at                                        O
                              838                       B-depart_time.time
                               am                       I-depart_time.time
                              and                                        O
                           arrive                                        O
                               in                                        O
                           denver                        B-toloc.city_name
                               at                                        O
                             1110                       B-arrive_time.time
                               in                                        O
                              the                                        O
                          morning              B-arrive_time.period_of_day
                              EOS                                        O
**************************************************************************
   1:         flight: BOS what flights are available from pittsburgh to baltimore on thursday morning EOS
                              BOS                                        O
                             what                                        O
                          flights                                        O
                              are                                        O
                        available                                        O
                             from                                        O
                       pittsburgh                      B-fromloc.city_name
                               to                                        O
                        baltimore                        B-toloc.city_name
                               on                                        O
                         thursday                   B-depart_date.day_name
                          morning              B-depart_time.period_of_day
                              EOS                                        O
**************************************************************************
   2:    flight_time: BOS what is the arrival time in san francisco for the 755 am flight leaving washington EOS
                              BOS                                        O
                             what                                        O
                               is                                        O
                              the                                        O
                          arrival                            B-flight_time
                             time                            I-flight_time
                               in                                        O
                              san                      B-fromloc.city_name
                        francisco                      I-fromloc.city_name
                              for                                        O
                              the                                        O
                              755                       B-depart_time.time
                               am                       I-depart_time.time
                           flight                                        O
                          leaving                                        O
                       washington                      B-fromloc.city_name
                              EOS                                        O
**************************************************************************
   3:        airfare: BOS cheapest airfare from tacoma to orlando EOS
                              BOS                                        O
                         cheapest                          B-cost_relative
                          airfare                                        O
                             from                                        O
                           tacoma                      B-fromloc.city_name
                               to                                        O
                          orlando                        B-toloc.city_name
                              EOS                                        O
**************************************************************************
   4:        airfare: BOS round trip fares from pittsburgh to philadelphia under 1000 dollars EOS
                              BOS                                        O
                            round                             B-round_trip
                             trip                             I-round_trip
                            fares                                        O
                             from                                        O
                       pittsburgh                      B-fromloc.city_name
                               to                                        O
                     philadelphia                        B-toloc.city_name
                            under                          B-cost_relative
                             1000                            B-fare_amount
                          dollars                            I-fare_amount
                              EOS                                        O
**************************************************************************
   5:         flight: BOS i need a flight tomorrow from columbus to minneapolis EOS
                              BOS                                        O
                                i                                        O
                             need                                        O
                                a                                        O
                           flight                                        O
                         tomorrow             B-depart_date.today_relative
                             from                                        O
                         columbus                      B-fromloc.city_name
                               to                                        O
                      minneapolis                        B-toloc.city_name
                              EOS                                        O
**************************************************************************
   6:       aircraft: BOS what kind of aircraft is used on a flight from cleveland to dallas EOS
                              BOS                                        O
                             what                                        O
                             kind                                        O
                               of                                        O
                         aircraft                                        O
                               is                                        O
                             used                                        O
                               on                                        O
                                a                                        O
                           flight                                        O
                             from                                        O
                        cleveland                      B-fromloc.city_name
                               to                                        O
                           dallas                        B-toloc.city_name
                              EOS                                        O
**************************************************************************
   7:         flight: BOS show me the flights from pittsburgh to los angeles on thursday EOS
                              BOS                                        O
                             show                                        O
                               me                                        O
                              the                                        O
                          flights                                        O
                             from                                        O
                       pittsburgh                      B-fromloc.city_name
                               to                                        O
                              los                        B-toloc.city_name
                          angeles                        I-toloc.city_name
                               on                                        O
                         thursday                   B-depart_date.day_name
                              EOS                                        O
**************************************************************************
   8:         flight: BOS all flights from boston to washington EOS
                              BOS                                        O
                              all                                        O
                          flights                                        O
                             from                                        O
                           boston                      B-fromloc.city_name
                               to                                        O
                       washington                        B-toloc.city_name
                              EOS                                        O
**************************************************************************
   9: ground_service: BOS what kind of ground transportation is available in denver EOS
                              BOS                                        O
                             what                                        O
                             kind                                        O
                               of                                        O
                           ground                                        O
                   transportation                                        O
                               is                                        O
                        available                                        O
                               in                                        O
                           denver                              B-city_name
                              EOS                                        O
**************************************************************************
  10:         flight: BOS show me the flights from dallas to san francisco EOS
                              BOS                                        O
                             show                                        O
                               me                                        O
                              the                                        O
                          flights                                        O
                             from                                        O
                           dallas                      B-fromloc.city_name
                               to                                        O
                              san                        B-toloc.city_name
                        francisco                        I-toloc.city_name
                              EOS                                        O
**************************************************************************
  11:         flight: BOS show me the flights from san diego to newark by way of houston EOS
                              BOS                                        O
                             show                                        O
                               me                                        O
                              the                                        O
                          flights                                        O
                             from                                        O
                              san                      B-fromloc.city_name
                            diego                      I-fromloc.city_name
                               to                                        O
                           newark                        B-toloc.city_name
                               by                                        O
                              way                                        O
                               of                                        O
                          houston                      B-stoploc.city_name
                              EOS                                        O
**************************************************************************
  12:        airport: BOS what 's the airport at orlando EOS
                              BOS                                        O
                             what                                        O
                               's                                        O
                              the                                        O
                          airport                                        O
                               at                                        O
                          orlando                              B-city_name
                              EOS                                        O
**************************************************************************
  13:         flight: BOS what is the cheapest flight from boston to bwi EOS
                              BOS                                        O
                             what                                        O
                               is                                        O
                              the                                        O
                         cheapest                          B-cost_relative
                           flight                                        O
                             from                                        O
                           boston                      B-fromloc.city_name
                               to                                        O
                              bwi                     B-toloc.airport_code
                              EOS                                        O
**************************************************************************
  14:         flight: BOS all flights to baltimore after 6 pm EOS
                              BOS                                        O
                              all                                        O
                          flights                                        O
                               to                                        O
                        baltimore                        B-toloc.city_name
                            after              B-depart_time.time_relative
                                6                       B-depart_time.time
                               pm                       I-depart_time.time
                              EOS                                        O
**************************************************************************
```

### Rasa NLU JSON format
```json
{
    "rasa_nlu_data": {
        "common_examples": [
            {
                "text": "i would like to find a flight from charlotte to las vegas that makes a stop in st. louis",
                "intent": "flight",
                "entities": [
                    {
                        "start": 35,
                        "end": 44,
                        "value": "charlotte",
                        "entity": "fromloc.city_name"
                    },
                    {
                        "start": 48,
                        "end": 57,
                        "value": "las vegas",
                        "entity": "toloc.city_name"
                    },
                    {
                        "start": 79,
                        "end": 88,
                        "value": "st. louis",
                        "entity": "stoploc.city_name"
                    }
                ]
            },
            ...
        ]
    }
}
```

## Summary of Data
| Sample Number | Vocabulary Size | Number of Slots | Number of Intents |
| --- | --- | --- | --- |
| 4978(Training set)+893(Testing set) | 943 | 129 | 26 |

## Sample Code
[summary_data.py](summary_data.py) include codes to read data from raw data file，user can learn how to read data.

## Download Data

| Data Format | Training Set | Testing Set |
| --- | --- | --- |
| Python 3 Pickle Format | [atis.train.pkl](data/raw_data/ms-cntk-atis/atis.train.pkl) | [atis.test.pkl](data/raw_data/ms-cntk-atis/atis.test.pkl) |
| Rasa NLU JSON Format | [train.json](data/standard_format/rasa/train.json) | [test.json](data/standard_format/rasa/test.json) |



## Credit
* The origin data set come from [ATIS DataSet by siddhadev](https://www.kaggle.com/siddhadev/atis-dataset)，some codes also copied from here。
    * NOTE: `ATIS DataSet by siddhadev` comes from [MicroSoft CNTK Examples](https://github.com/Microsoft/CNTK/tree/master/Examples/LanguageUnderstanding/ATIS/Data)

## Similar Projects
* https://github.com/mesnilgr/is13 also provide ATIS dataset, but only provide slots data without intent.
