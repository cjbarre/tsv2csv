# tsv2csv
A TSV to CSV command line tool powered by Clojure

## Rationale

I created this to satisfy a personal need to convert TSV to CSV and I had a previous implementation of the same functionality laying around in a fully fledged Clojure project. I'd rather write a smidge of LISP sometimes than use existing tools with wonky interfaces like sed and awk ( sorry :-) ).

## Features

- Replaces tabs with commas
- Trims whitespace around values
- Wraps all values in double quotes

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

=>

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

## Dependencies

- Clojure CLI: https://clojure.org/guides/getting_started

## Platforms

- Linux

## Performance

At the time I was creating a pipeline to automatically generate BLS databases from TSV dumps. This tool is designed to be used in a streaming pipeline, which you can see a real example of above. 

It may depend on your network bandwidth, but for me in a pipeline with wget and pgfutter for loading a CSV into PostgreSQL, a TSV file with over seven million rows flows from the remote server into my database in around one minute. 

I use tsv2csv with GNU parallel to create / load every table in the database as quickly as possible in a single pass.

I'll have to check soon how fast the pipeline goes when the entire data file is already on the local system.

## Bugs & Suggestions

Create an issue if you find yourself using this and have trouble or have an idea.

## Roadmap

- Add a help option
- Notify when called without input
- Test on dataset larger than 7 million rows

## License

License is MIT

## Maintainer

Cameron Barre
