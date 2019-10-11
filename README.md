# tsv2csv
A TSV to CSV command line tool powered by Clojure

## Rationale

I created this to satisfy a personal need to convert TSV to CSV and I had a previous implementation of the same functionality laying around in a fully fledged Clojure project. I'd rather right a smidge of LISP sometimes than use existing tools with wonky interfaces like sed and awk ( sorry :-) ).

## Dependencies

- Clojure CLI: https://clojure.org/guides/getting_started

## Platforms

- Linux

## Bugs

Create an issue if you find yourself using this and have trouble.

## License

License is MIT

## Usage

Sample Example:

```
echo -e $(cat sample.tsv) | ./tsv2csv

=>

"hello","world"
"hello","world, with commas"
```

Real Example using BLS data:

```
wget https://download.bls.gov/pub/time.series/ce/ce.datatype -q -O - | ./tsv2csv

"data_type_code","data_type_text"
"01","ALL EMPLOYEES, THOUSANDS"
"02","AVERAGE WEEKLY HOURS OF ALL EMPLOYEES"
"03","AVERAGE HOURLY EARNINGS OF ALL EMPLOYEES"
"04","AVERAGE WEEKLY OVERTIME HOURS OF ALL EMPLOYEES"
"06","PRODUCTION AND NONSUPERVISORY EMPLOYEES, THOUSANDS"
"07","AVERAGE WEEKLY HOURS OF PRODUCTION AND NONSUPERVISORY EMPLOYEES"
"08","AVERAGE HOURLY EARNINGS OF PRODUCTION AND NONSUPERVISORY EMPLOYEES"
"09","AVERAGE WEEKLY OVERTIME HOURS OF PRODUCTION AND NONSUPERVISORY EMPLOYEES"
...
```