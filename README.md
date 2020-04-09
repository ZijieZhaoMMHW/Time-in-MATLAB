Time in MATLAB
==============

Time in MATLAB is relatively hard to understand. For example, if you want to get "13 - Mar - 2019" in MATLAB in numerical way, you would get something like:

```
datenum(2019,3,13,0,0,0) % generating numerical time values corresponding to 00:00:00 on 13 - Mar - 2019

ans =

      737497
```

This strange number actually represents the whole and fractional number of days from a fixed, preset date (January 0, 0000) in the proleptic ISO calendar. That is why there is such a large number.

In this assignment, Claire asked you to performance half - hour averaging on the ‘High- Frequency data’ (10 HZ). It means your resultant vector should be a time series with 48 elements, each of which corresponds to a particular time segment. 

```
Element 1 - 00:00:00 ~ 00:30:00
Element 2 - 00:30:00 ~ 01:00:00
......
Element 48 - 23:30:00 ~ 24:00:00
```

For your resultant half - hour averaging time series, you can see that each element of it is not corresponding to a single time point, it is corresponding to a half - hour time period. However, if you want to draw plots in MATLAB, you have to make your data in x - axis and y - axis shares the same length. For example:

```
x=1:10
x =

     1     2     3     4     5     6     7     8     9    10
y=1:10

y =

     1     2     3     4     5     6     7     8     9    10
length(x)
ans =

    10
length(y)
ans =

    10
plot(x,y)
```
![Image text](https://github.com/ZijieZhaoMMHW/Time-in-MATLAB/blob/master/normal_plot.png)

If x and y have different length, you gonna get an error
```
x=1:10
x =

     1     2     3     4     5     6     7     8     9    10
y=1:11

y =

     1     2     3     4     5     6     7     8     9    10    11
length(x)
ans =

    10
length(y)
ans =

    11
plot(x,y)

Error!
```

Therefore, you need to get a 48 - elements timestamp series to plot your half - hour avergaing data. This means you need to use 48 time points to represent the 48 half - hour time periods. 

This question can be simplified as using 48 representative time points to represent these 48 half - hour time periods. Normally, we use the central time of each time period to represent the full period.

```
Element 1: 00:00:00 ~ 00:30:00 -- 00:15:00
Element 2: 00:30:00 ~ 01:00:00 -- 00:45:00
...
Element 48: 23:30:00 ~ 24:00:00 -- 23:45:00
```

So you need to construct a time series, from 00:15:00 to 23:45:00 by 30 minutes.

```
Timestamp_plot=datenum(2019,3,13,0,15,0):1/48:datenum(2019,3,13,23,45,0); %1/48 is the fraction of 30 minutes with respect to 24 hours.
```
