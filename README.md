# ARCHIVED
This has been replaced by the [FreeAgent CSV Formatter](https://fcf.v.robbie.dev/).

# marcus2freeagent
Convert Marcus CSV format to be imported by FreeAgent 


# Motivation

I signed up to the Marcus Savings account and while trying to add it to FreeAgent, I realised that there are no native feeds supported, nor support for OFX or QIF which FreeAgent also supports.
The only option was CSV, but even then the format was not quite the same. The Marcus CSV format has much more detail and the column order does not match what FreeAgent supports.

After checking the CSV format that FreeAgent expects [here](https://support.freeagent.com/hc/en-us/articles/115001222564)
I wrote this basic tool to help me convert the CSV statements from Marcus for direct import into FreeAgent.

## Usage

Start with a CSV statement generated by Marcus.
The current CSV format is this:


```
$ cat sample.csv
"TransactionDate","Description","Value","AccountBalance","AccountName","AccountNumber"
"20201016","Interest applied","3.75","5010.87"," Marcus Savings","12345678"
"20200928","Withdrawal to 01234567","-6000.00","5007.12"," Marcus Savings","12345678"
```

Then run 

```
./m2f.py sample.csv
```


This will generate a FreeAgent version of the file with the prefix `fa-`

```
$ cat fa-sample.csv
16/10/2020,3.75,Interest applied
28/09/2020,-6000.00,Withdrawal to 01234567
```
