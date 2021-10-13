# Found this test from a company looking to hire someone.

The task was to find the `f1 score` of tuesdays in the dataset. The file
was labeled as a `.psv` file. I decided ill just run `cat` to see if
there was anything in it. Turns out `psv` is pipe separated variable.
Once i found out that there was data in the file in a "csv" like file i
moved to python. Using the datetime library, csv and sklearn i was able to
filter out all lines that were tuesdays and then run the `f1 score`
across them. The code took 20 minutes to write which i was quite happy
with. The code is shown below. I iteratively tested using ipython which
was easy to work with.

```python

import datetime
import csv
from sklearn.metrics import f1_score
with open('test_v2.psv', newline='') as csvf:
    file = csv.reader(csvf, delimiter='|')
        tuesdays=[]
        for i, row in enumerate(file):
            if i == 0:
                pass
            elif i == 1:
                pass
            else:
    
                col1=row[0].split('-')
                d = datetime(int(col1[0]), int(col1[1]), int(col1[2]))
                if d.weekday() == 1:
                    tuesdays.append(row)
    
    
    print(f'Days : {tuesdays}')
    y = []
    y_hat = []
    for item in tuesdays:
        y.append(int(item[1]))
        y_hat.append(int(item[2]))
    res = f1_score(y,y_hat)


```



I wasn't certain of the answer i got having thrown the solution
together and so i thought i would manually run the f1 measurement. I
needed to clean up the data to feed it into libre office and this was
where my bash learning came in handy. Using a while loop, parameter
substitution, process substitution and sending the results to a new file
i was able to convert the psv into a csv file. Admittedly it looked for
all `|` and if there was any outside of the main data it would change
that too. But i wasn't worried. The shell line i wrote is seen below.

```bash
while read line; do string=${line//|/,}; echo $string; echo $string >> test3.csv; done < <(cat test_v2.psv)
```

Once this was done i opened it up in libreoffice and calculated the
result. I like that i was able to use my bash skills to run a fast file
modification to allow the program to run in libreoffice and am keen to
try more of these.


    #python #bash #funcoding

