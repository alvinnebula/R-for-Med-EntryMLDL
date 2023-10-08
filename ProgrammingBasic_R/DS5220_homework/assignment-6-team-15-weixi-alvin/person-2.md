Person 2
================
Yiwen Chen

## Lubridate

The interview dataset is “survey data relating to households and
agriculture in Tanzania and Mozambique. The survey data was collected
through interviews conducted between November 2016 and June 2017 using
forms downloaded to Android Smartphones.” The variable `start` is the
date and time of the start of the interview, and `end` is the date and
time the interview ended.

[Source](https://datacarpentry.org/socialsci-workshop/data/)

``` r
interview <- read.csv("interview.csv")
View(interview)
```

1.  Parse `start` and `end` using lubridate functions into two new
    columns. Put the new columns at the front of the dataset, along with
    the `start` and `end` columns.

``` r
interview$new_start <- ymd_hms(interview$start)
interview$new_end <- ymd_hms(interview$end)

new_interview <- interview %>% 
  select(new_start, new_end, start, end, everything())
new_interview
```

    ##               new_start             new_end               start
    ## 1   2017-03-23 09:49:57 2017-04-02 17:29:08 2017-03-23 09:49:57
    ## 2   2017-04-02 09:48:16 2017-04-02 17:26:19 2017-04-02 09:48:16
    ## 3   2017-04-02 14:35:26 2017-04-02 17:26:53 2017-04-02 14:35:26
    ## 4   2017-04-02 14:55:18 2017-04-02 17:27:16 2017-04-02 14:55:18
    ## 5   2017-04-02 15:10:35 2017-04-02 17:27:35 2017-04-02 15:10:35
    ## 6   2017-04-02 15:27:25 2017-04-02 17:28:02 2017-04-02 15:27:25
    ## 7   2017-04-02 15:38:01 2017-04-02 17:28:19 2017-04-02 15:38:01
    ## 8   2017-04-02 15:59:52 2017-04-02 17:28:39 2017-04-02 15:59:52
    ## 9   2017-04-02 16:23:36 2017-04-02 16:42:08 2017-04-02 16:23:36
    ## 10  2017-04-02 17:03:28 2017-04-02 17:25:11 2017-04-02 17:03:28
    ## 11  2017-04-03 03:16:15 2017-04-03 03:31:10 2017-04-03 03:16:15
    ## 12  2017-04-03 03:31:13 2017-04-03 03:58:34 2017-04-03 03:31:13
    ## 13  2017-04-03 03:58:43 2017-04-03 04:19:36 2017-04-03 03:58:43
    ## 14  2017-04-03 04:19:57 2017-04-03 04:50:05 2017-04-03 04:19:57
    ## 15  2017-04-03 05:12:17 2017-04-03 05:28:44 2017-04-03 05:12:17
    ## 16  2017-04-03 05:29:24 2017-04-03 05:40:53 2017-04-03 05:29:24
    ## 17  2017-04-03 05:41:42 2017-04-03 05:57:57 2017-04-03 05:41:42
    ## 18  2017-04-03 12:27:04 2017-04-03 12:39:48 2017-04-03 12:27:04
    ## 19  2017-04-03 12:40:14 2017-04-03 12:53:29 2017-04-03 12:40:14
    ## 20  2017-04-03 14:04:50 2017-04-03 14:20:04 2017-04-03 14:04:50
    ## 21  2017-04-03 14:24:58 2017-04-03 14:44:39 2017-04-03 14:24:58
    ## 22  2017-04-03 16:28:52 2017-04-03 16:40:47 2017-04-03 16:28:52
    ## 23  2017-04-03 16:41:04 2017-04-03 17:04:28 2017-04-03 16:41:04
    ## 24  2017-04-03 17:19:49 2017-04-03 17:43:01 2017-04-03 17:19:49
    ## 25  2017-04-04 04:01:58 2017-04-04 04:29:47 2017-04-04 04:01:58
    ## 26  2017-04-04 04:30:19 2017-04-04 04:44:19 2017-04-04 04:30:19
    ## 27  2017-04-05 04:59:42 2017-04-05 05:14:45 2017-04-05 04:59:42
    ## 28  2017-04-05 05:14:49 2017-04-05 05:36:18 2017-04-05 05:14:49
    ## 29  2017-04-05 05:37:30 2017-04-05 06:05:44 2017-04-05 05:37:30
    ## 30  2017-04-05 06:05:58 2017-04-05 06:20:39 2017-04-05 06:05:58
    ## 31  2017-04-05 06:21:20 2017-04-05 06:38:26 2017-04-05 06:21:20
    ## 32  2017-04-05 06:38:55 2017-04-05 08:05:32 2017-04-05 06:38:55
    ## 33  2017-04-05 08:08:19 2017-04-05 08:25:48 2017-04-05 08:08:19
    ## 34  2017-04-05 16:00:47 2017-04-05 16:21:59 2017-04-05 16:00:47
    ## 35  2017-04-05 16:22:13 2017-04-05 16:50:25 2017-04-05 16:22:13
    ## 36  2017-04-05 16:50:48 2017-04-05 17:10:53 2017-04-05 16:50:48
    ## 37  2017-04-05 17:17:48 2017-04-05 17:26:51 2017-04-05 17:17:48
    ## 38  2017-04-05 17:28:12 2017-04-05 17:50:57 2017-04-05 17:28:12
    ## 39  2017-04-06 08:31:17 2017-04-06 08:44:47 2017-04-06 08:31:17
    ## 40  2017-04-06 08:44:51 2017-04-06 09:03:47 2017-04-06 08:44:51
    ## 41  2017-04-06 09:03:50 2017-04-06 09:14:05 2017-04-06 09:03:50
    ## 42  2017-04-06 09:14:22 2017-04-06 09:30:54 2017-04-06 09:14:22
    ## 43  2017-04-06 09:31:56 2017-04-06 09:53:53 2017-04-06 09:31:56
    ## 44  2017-04-06 14:44:32 2017-04-06 14:53:01 2017-04-06 14:44:32
    ## 45  2017-04-06 14:53:04 2017-04-06 15:11:57 2017-04-06 14:53:04
    ## 46  2017-04-06 15:19:41 2017-04-06 15:45:32 2017-04-06 15:19:41
    ## 47  2017-04-07 14:05:25 2017-04-07 14:19:45 2017-04-07 14:05:25
    ## 48  2017-04-07 14:19:49 2017-04-07 14:40:23 2017-04-07 14:19:49
    ## 49  2017-04-07 14:43:09 2017-04-07 14:55:51 2017-04-07 14:43:09
    ## 50  2017-04-07 14:56:01 2017-04-07 15:26:23 2017-04-07 14:56:01
    ## 51  2017-04-07 15:27:45 2017-04-07 15:39:10 2017-04-07 15:27:45
    ## 52  2017-04-08 04:44:09 2017-04-08 05:02:58 2017-04-08 04:44:09
    ## 53  2017-04-08 05:03:08 2017-04-08 05:33:51 2017-04-08 05:03:08
    ## 54  2017-04-08 05:36:55 2017-04-08 05:52:15 2017-04-08 05:36:55
    ## 55  2017-04-08 05:52:32 2017-04-08 06:05:41 2017-04-08 05:52:32
    ## 56  2017-04-08 06:05:59 2017-04-08 06:26:12 2017-04-08 06:05:59
    ## 57  2017-04-08 06:26:22 2017-04-08 06:39:40 2017-04-08 06:26:22
    ## 58  2017-04-08 08:25:49 2017-04-08 08:48:51 2017-04-08 08:25:49
    ## 59  2017-04-08 08:52:05 2017-04-08 09:02:34 2017-04-08 08:52:05
    ## 60  2017-04-08 09:03:01 2017-04-08 09:20:18 2017-04-08 09:03:01
    ## 61  2017-04-08 10:47:11 2017-04-08 11:14:09 2017-04-08 10:47:11
    ## 62  2017-04-08 13:27:58 2017-04-08 13:41:21 2017-04-08 13:27:58
    ## 63  2017-04-08 13:41:39 2017-04-08 13:52:07 2017-04-08 13:41:39
    ## 64  2017-04-08 13:52:30 2017-04-08 14:02:24 2017-04-08 13:52:30
    ## 65  2017-04-08 14:02:49 2017-04-08 14:15:45 2017-04-08 14:02:49
    ## 66  2017-04-08 21:09:38 2017-04-08 21:33:45 2017-04-08 21:09:38
    ## 67  2017-04-08 21:34:23 2017-04-08 21:49:02 2017-04-08 21:34:23
    ## 68  2017-04-08 21:49:40 2017-04-09 22:06:57 2017-04-08 21:49:40
    ## 69  2017-04-09 22:08:07 2017-04-09 22:21:08 2017-04-09 22:08:07
    ## 70  2017-04-09 22:21:23 2017-04-09 22:40:57 2017-04-09 22:21:23
    ## 71  2017-04-09 15:00:19 2017-04-09 15:19:22 2017-04-09 15:00:19
    ## 72  2017-04-09 05:16:06 2017-04-09 05:27:41 2017-04-09 05:16:06
    ## 73  2017-04-09 05:27:46 2017-04-09 05:43:51 2017-04-09 05:27:46
    ## 74  2017-04-09 05:47:31 2017-04-09 06:16:11 2017-04-09 05:47:31
    ## 75  2017-04-09 06:16:49 2017-04-09 06:28:48 2017-04-09 06:16:49
    ## 76  2017-04-09 06:35:16 2017-04-09 06:48:01 2017-04-09 06:35:16
    ## 77  2017-04-09 06:54:49 2017-04-09 07:14:16 2017-04-09 06:54:49
    ## 78  2017-04-09 07:59:49 2017-04-09 08:22:34 2017-04-09 07:59:49
    ## 79  2017-04-09 08:23:05 2017-04-09 08:42:02 2017-04-09 08:23:05
    ## 80  2017-04-09 08:43:08 2017-04-09 09:07:48 2017-04-09 08:43:08
    ## 81  2017-04-09 09:08:04 2017-04-09 09:34:12 2017-04-09 09:08:04
    ## 82  2017-04-09 15:20:26 2017-04-09 15:46:14 2017-04-09 15:20:26
    ## 83  2017-04-09 15:48:14 2017-04-09 16:12:46 2017-04-09 15:48:14
    ## 84  2017-04-09 16:13:19 2017-04-09 16:35:24 2017-04-09 16:13:19
    ## 85  2017-04-09 18:00:41 2017-04-09 18:31:40 2017-04-09 18:00:41
    ## 86  2017-04-09 18:32:09 2017-04-09 19:14:52 2017-04-09 18:32:09
    ## 87  2017-04-09 19:15:21 2017-04-09 19:27:56 2017-04-09 19:15:21
    ## 88  2017-04-09 19:31:47 2017-04-09 19:45:38 2017-04-09 19:31:47
    ## 89  2017-04-09 19:48:09 2017-04-09 20:08:15 2017-04-09 19:48:09
    ## 90  2017-04-26 15:46:24 2017-04-26 16:13:33 2017-04-26 15:46:24
    ## 91  2017-04-26 16:13:50 2017-04-26 16:45:01 2017-04-26 16:13:50
    ## 92  2017-04-26 16:45:28 2017-04-26 17:26:21 2017-04-26 16:45:28
    ## 93  2017-04-27 12:27:31 2017-04-27 12:56:42 2017-04-27 12:27:31
    ## 94  2017-04-27 12:58:02 2017-04-27 13:23:06 2017-04-27 12:58:02
    ## 95  2017-04-27 16:11:23 2017-04-27 16:41:41 2017-04-27 16:11:23
    ## 96  2017-04-27 16:42:02 2017-04-27 18:11:54 2017-04-27 16:42:02
    ## 97  2017-04-27 17:38:53 2017-04-27 18:09:45 2017-04-27 17:38:53
    ## 98  2017-04-28 06:27:07 2017-04-28 06:52:04 2017-04-28 06:27:07
    ## 99  2017-04-28 07:09:39 2017-04-28 07:31:38 2017-04-28 07:09:39
    ## 100 2017-04-28 09:01:47 2017-04-28 09:25:51 2017-04-28 09:01:47
    ## 101 2017-04-28 14:25:13 2017-04-28 15:18:10 2017-04-28 14:25:13
    ## 102 2017-04-28 15:32:38 2017-04-28 15:58:10 2017-04-28 15:32:38
    ## 103 2017-04-30 05:51:18 2017-04-30 06:47:01 2017-04-30 05:51:18
    ## 104 2017-05-03 13:14:43 2017-05-03 13:37:53 2017-05-03 13:14:43
    ## 105 2017-05-03 13:37:57 2017-05-03 13:58:06 2017-05-03 13:37:57
    ## 106 2017-05-03 14:00:13 2017-05-03 14:27:03 2017-05-03 14:00:13
    ## 107 2017-05-04 10:26:35 2017-05-04 10:46:35 2017-05-04 10:26:35
    ## 108 2017-05-04 10:47:05 2017-05-04 11:16:05 2017-05-04 10:47:05
    ## 109 2017-05-04 11:16:57 2017-05-04 11:38:38 2017-05-04 11:16:57
    ## 110 2017-05-11 05:24:25 2017-05-11 05:41:56 2017-05-11 05:24:25
    ## 111 2017-05-11 05:42:08 2017-05-11 06:08:58 2017-05-11 05:42:08
    ## 112 2017-05-11 06:09:56 2017-05-11 06:22:19 2017-05-11 06:09:56
    ## 113 2017-05-11 06:28:02 2017-05-11 06:55:35 2017-05-11 06:28:02
    ## 114 2017-05-18 04:36:23 2017-05-18 05:02:38 2017-05-18 04:36:23
    ## 115 2017-05-18 05:55:04 2017-05-18 06:37:10 2017-05-18 05:55:04
    ## 116 2017-05-18 10:37:37 2017-05-18 10:56:00 2017-05-18 10:37:37
    ## 117 2017-05-18 10:56:16 2017-05-18 11:07:35 2017-05-18 10:56:16
    ## 118 2017-06-03 05:08:49 2017-06-03 05:32:19 2017-06-03 05:08:49
    ## 119 2017-06-03 05:32:33 2017-06-03 05:51:49 2017-06-03 05:32:33
    ## 120 2017-06-03 05:53:28 2017-06-03 06:25:06 2017-06-03 05:53:28
    ## 121 2017-06-03 06:25:09 2017-06-03 06:45:06 2017-06-03 06:25:09
    ## 122 2017-06-03 06:50:47 2017-06-03 07:20:21 2017-06-03 06:50:47
    ## 123 2017-06-03 07:21:48 2017-06-03 07:51:29 2017-06-03 07:21:48
    ## 124 2017-06-03 15:23:01 2017-06-03 15:53:10 2017-06-03 15:23:01
    ## 125 2017-06-03 15:54:03 2017-06-03 16:17:26 2017-06-03 15:54:03
    ## 126 2017-06-03 16:17:55 2017-06-03 17:16:39 2017-06-03 16:17:55
    ## 127 2017-05-18 04:13:37 2017-05-18 04:35:47 2017-05-18 04:13:37
    ## 128 2017-06-04 09:36:20 2017-06-04 10:13:32 2017-06-04 09:36:20
    ## 129 2017-06-04 10:13:36 2017-06-04 10:32:06 2017-06-04 10:13:36
    ## 130 2017-06-04 10:33:55 2017-06-04 10:52:22 2017-06-04 10:33:55
    ## 131 2017-06-04 10:52:46 2017-06-04 11:08:13 2017-06-04 10:52:46
    ##                     end  id   interview_date quest_no province district    ward
    ## 1   2017-04-02 17:29:08   1 17 November 2016        1   Manica   Manica Bandula
    ## 2   2017-04-02 17:26:19   2 17 November 2016        1   Manica   Manica Bandula
    ## 3   2017-04-02 17:26:53   3 17 November 2016        3   Manica   Manica Bandula
    ## 4   2017-04-02 17:27:16   4 17 November 2016        4   Manica   Manica Bandula
    ## 5   2017-04-02 17:27:35   5 17 November 2016        5   Manica   Manica Bandula
    ## 6   2017-04-02 17:28:02   6 17 November 2016        6   Manica   Manica Bandula
    ## 7   2017-04-02 17:28:19   7 17 November 2016        7   Manica   Manica Bandula
    ## 8   2017-04-02 17:28:39   8 16 November 2016        8   Manica   Manica  Manica
    ## 9   2017-04-02 16:42:08   9 16 November 2016        9   Manica   Manica Bandula
    ## 10  2017-04-02 17:25:11  10 16 December 2016       10   Manica   Manica Bandula
    ## 11  2017-04-03 03:31:10  11 21 November 2016       11   Manica   Manica Bandula
    ## 12  2017-04-03 03:58:34  12 21 November 2016       12   Manica   Manica Bandula
    ## 13  2017-04-03 04:19:36  13 21 November 2016       13   Manica   Manica Bandula
    ## 14  2017-04-03 04:50:05  14 21 November 2016       14   Manica   Manica Bandula
    ## 15  2017-04-03 05:28:44  15 21 November 2016       15   Manica   Manica Bandula
    ## 16  2017-04-03 05:40:53  16 24 November 2016       16   Manica   Manica Bandula
    ## 17  2017-04-03 05:57:57  17 21 November 2016       17   Manica   Manica Bandula
    ## 18  2017-04-03 12:39:48  18 21 November 2016       18   Manica   Manica Bandula
    ## 19  2017-04-03 12:53:29  19 21 November 2016       19   Manica   Manica Bandula
    ## 20  2017-04-03 14:20:04  20 21 November 2016       20   Manica   Manica Bandula
    ## 21  2017-04-03 14:44:39  21 21 November 2016       21   Manica   Manica Bandula
    ## 22  2017-04-03 16:40:47  22 21 November 2016       22   Manica   Manica Bandula
    ## 23  2017-04-03 17:04:28  23 21 November 2016       23   Manica   Manica Bandula
    ## 24  2017-04-03 17:43:01  24 21 November 2016       24   Manica   Manica Bandula
    ## 25  2017-04-04 04:29:47  25 21 November 2016       25   Manica   Manica Bandula
    ## 26  2017-04-04 04:44:19  26 21 November 2016       26   Manica   Manica Bandula
    ## 27  2017-04-05 05:14:45  27 21 November 2016       27   Manica   Manica Bandula
    ## 28  2017-04-05 05:36:18  28 21 November 2016       28   Manica   Manica Bandula
    ## 29  2017-04-05 06:05:44  29 21 November 2016       29   Manica   Manica Bandula
    ## 30  2017-04-05 06:20:39  30 21 November 2016       30   Manica   Manica Bandula
    ## 31  2017-04-05 06:38:26  31 21 November 2016       31   Manica   Manica Bandula
    ## 32  2017-04-05 08:05:32  32 21 November 2016       32   Manica   Manica Bandula
    ## 33  2017-04-05 08:25:48  33 21 November 2016       33   Manica   Manica Bandula
    ## 34  2017-04-05 16:21:59  34 17 November 2016       34   Manica   Manica Bandula
    ## 35  2017-04-05 16:50:25  35 17 November 2016       35   Manica   Manica Bandula
    ## 36  2017-04-05 17:10:53  36 17 November 2016       36   Manica   Manica Bandula
    ## 37  2017-04-05 17:26:51  37 17 November 2016       37   Manica   Manica Bandula
    ## 38  2017-04-05 17:50:57  38 17 November 2016       38   Manica   Manica Bandula
    ## 39  2017-04-06 08:44:47  39 17 November 2016       39   Manica   Manica Bandula
    ## 40  2017-04-06 09:03:47  40 17 November 2016       40   Manica   Manica Bandula
    ## 41  2017-04-06 09:14:05  41 17 November 2016       41   Manica   Manica Bandula
    ## 42  2017-04-06 09:30:54  42 17 November 2016       42   Manica   Manica Bandula
    ## 43  2017-04-06 09:53:53  43 17 November 2016       43   Manica   Manica Bandula
    ## 44  2017-04-06 14:53:01  44 17 November 2016       44   Manica   Manica Bandula
    ## 45  2017-04-06 15:11:57  45 17 November 2016       45   Manica   Manica Bandula
    ## 46  2017-04-06 15:45:32  46 17 November 2016       46   Manica   Manica Bandula
    ## 47  2017-04-07 14:19:45  47 17 November 2016       47   Manica   Manica Bandula
    ## 48  2017-04-07 14:40:23  48 16 November 2016       48   Manica   Manica Bandula
    ## 49  2017-04-07 14:55:51  49 16 November 2016       49   Manica   Manica Bandula
    ## 50  2017-04-07 15:26:23  50 16 November 2016       50   Manica   Manica Bandula
    ## 51  2017-04-07 15:39:10  51 16 November 2016       51   Manica   Manica Bandula
    ## 52  2017-04-08 05:02:58  52 16 November 2016       52   Manica   Manica Bandula
    ## 53  2017-04-08 05:33:51  53 16 November 2016       21   Manica   Manica Bandula
    ## 54  2017-04-08 05:52:15  54 16 November 2016       54   Manica   Manica Bandula
    ## 55  2017-04-08 06:05:41  55 16 November 2016       55   Manica   Manica Bandula
    ## 56  2017-04-08 06:26:12  56 16 November 2016       56   Manica   Manica Bandula
    ## 57  2017-04-08 06:39:40  57 16 November 2016       57   Manica   Manica Bandula
    ## 58  2017-04-08 08:48:51  58 16 November 2016       58   Manica   Manica Bandula
    ## 59  2017-04-08 09:02:34  59 16 November 2016       59   Manica   Manica Bandula
    ## 60  2017-04-08 09:20:18  60 16 November 2016       60   Manica  Bandula Bandula
    ## 61  2017-04-08 11:14:09  61 16 November 2016       61   Manica   Manica Bandula
    ## 62  2017-04-08 13:41:21  62 16 November 2016       62   Manica   Manica Bandula
    ## 63  2017-04-08 13:52:07  63 16 November 2016       63   Manica   Manica Bandula
    ## 64  2017-04-08 14:02:24  64 16 November 2016       64   Manica   Manica Bandula
    ## 65  2017-04-08 14:15:45  65 16 November 2016       65   Manica   Manica Bandula
    ## 66  2017-04-08 21:33:45  66 16 November 2016       66   Manica   Manica Bandula
    ## 67  2017-04-08 21:49:02  67 16 November 2016       67   Manica   Manica Bandula
    ## 68  2017-04-09 22:06:57  68 16 November 2016       68   Manica   Manica Bandula
    ## 69  2017-04-09 22:21:08  69 16 November 2016       69   Manica   Manica Bandula
    ## 70  2017-04-09 22:40:57  70 16 November 2016       70   Manica   Manica Bandula
    ## 71  2017-04-09 15:19:22  71 18 November 2016       71   Manica   Manica Bandula
    ## 72  2017-04-09 05:27:41  72 16 November 2016      127   Manica   Manica Bandula
    ## 73  2017-04-09 05:43:51  73 23 November 2016      133   Manica   Manica Bandula
    ## 74  2017-04-09 06:16:11  74 24 November 2016      152   Manica   Manica Bandula
    ## 75  2017-04-09 06:28:48  75 24 November 2016      153   Manica   Manica Bandula
    ## 76  2017-04-09 06:48:01  76 24 November 2016      155   Manica   Manica Bandula
    ## 77  2017-04-09 07:14:16  77 25 November 2016      178   Manica   Manica Bandula
    ## 78  2017-04-09 08:22:34  78 25 November 2016      177   Manica   Manica Bandula
    ## 79  2017-04-09 08:42:02  79 25 November 2016      180   Manica   Manica Bandula
    ## 80  2017-04-09 09:07:48  80 25 November 2016      181   Manica   Manica Bandula
    ## 81  2017-04-09 09:34:12  81 25 November 2016      182   Manica   Manica Bandula
    ## 82  2017-04-09 15:46:14  82 28 November 2016      186   Manica   Manica  Manica
    ## 83  2017-04-09 16:12:46  83 28 November 2016      187   Manica   Manica Bandula
    ## 84  2017-04-09 16:35:24  84 28 November 2016      195   Manica   Manica Bandula
    ## 85  2017-04-09 18:31:40  85 28 November 2016      196   Manica   Manica Bandula
    ## 86  2017-04-09 19:14:52  86 28 November 2016      197   Manica   Manica Bandula
    ## 87  2017-04-09 19:27:56  87 28 November 2016      198   Manica   Manica Bandula
    ## 88  2017-04-09 19:45:38  88 21 November 2016      201   Manica   Manica Bandula
    ## 89  2017-04-09 20:08:15  89 17 November 2016      202   Manica   Manica Bandula
    ## 90  2017-04-26 16:13:33  90    26 April 2017       72   Manica   Manica Bandula
    ## 91  2017-04-26 16:45:01  91    26 April 2017       73   Manica   Manica Bandula
    ## 92  2017-04-26 17:26:21  92    26 April 2017       76   Manica   Manica Bandula
    ## 93  2017-04-27 12:56:42  93    27 April 2017       83   Manica   Manica Bandula
    ## 94  2017-04-27 13:23:06  94    27 April 2017       85   Manica   Manica Bandula
    ## 95  2017-04-27 16:41:41  95    27 April 2017       89   Manica   Manica Bandula
    ## 96  2017-04-27 18:11:54  96    27 April 2017      101   Manica   Manica Bandula
    ## 97  2017-04-27 18:09:45  97    27 April 2017      103   Manica   Manica Bandula
    ## 98  2017-04-28 06:52:04  98    28 April 2017      102   Manica   Manica Bandula
    ## 99  2017-04-28 07:31:38  99    28 April 2017       78   Manica   Manica Bandula
    ## 100 2017-04-28 09:25:51 100    28 April 2017       80   Manica   Manica Bandula
    ## 101 2017-04-28 15:18:10 101    28 April 2017      104   Manica   Manica Bandula
    ## 102 2017-04-28 15:58:10 102    28 April 2017      105   Manica   Manica Bandula
    ## 103 2017-04-30 06:47:01 103    30 April 2017      106   Manica   Manica Bandula
    ## 104 2017-05-03 13:37:53 104      03 May 2017      109   Manica   Manica Bandula
    ## 105 2017-05-03 13:58:06 105      03 May 2017      110   Manica   Manica Bandula
    ## 106 2017-05-03 14:27:03 106      03 May 2017      113   Manica   Manica Bandula
    ## 107 2017-05-04 10:46:35 107      04 May 2017      118   Manica   Manica Bandula
    ## 108 2017-05-04 11:16:05 108      04 May 2017      125   Manica   Manica Bandula
    ## 109 2017-05-04 11:38:38 109      04 May 2017      119   Manica   Manica Bandula
    ## 110 2017-05-11 05:41:56 110      11 May 2017      115   Manica   Manica Bandula
    ## 111 2017-05-11 06:08:58 111      11 May 2017      108   Manica   Manica Bandula
    ## 112 2017-05-11 06:22:19 112      11 May 2017      116   Manica   Manica Bandula
    ## 113 2017-05-11 06:55:35 113      11 May 2017      117   Manica   Manica Bandula
    ## 114 2017-05-18 05:02:38 114      18 May 2017      144   Manica   Manica Bandula
    ## 115 2017-05-18 06:37:10 115      18 May 2017      143   Manica   Manica Bandula
    ## 116 2017-05-18 10:56:00 116      18 May 2017      150   Manica   Manica Bandula
    ## 117 2017-05-18 11:07:35 117      18 May 2017      159   Manica   Manica Bandula
    ## 118 2017-06-03 05:32:19 118     03 June 2017      160   Manica   Manica Bandula
    ## 119 2017-06-03 05:51:49 119     03 June 2017      165   Manica   Manica Bandula
    ## 120 2017-06-03 06:25:06 120     03 June 2017      166   Manica   Manica Bandula
    ## 121 2017-06-03 06:45:06 121     03 June 2017      167   Manica   Manica Bandula
    ## 122 2017-06-03 07:20:21 122     03 June 2017      174   Manica   Manica Bandula
    ## 123 2017-06-03 07:51:29 123     03 June 2017      175   Manica   Manica Bandula
    ## 124 2017-06-03 15:53:10 124     03 June 2017      189   Manica   Manica Bandula
    ## 125 2017-06-03 16:17:26 125     03 June 2017      191   Manica   Manica Bandula
    ## 126 2017-06-03 17:16:39 126     03 June 2017      192   Manica   Manica Bandula
    ## 127 2017-05-18 04:35:47 127      18 May 2017      126   Manica   Manica Bandula
    ## 128 2017-06-04 10:13:32 128     04 June 2017      193   Manica   Manica Bandula
    ## 129 2017-06-04 10:32:06 129     04 June 2017      194   Manica   Manica Bandula
    ## 130 2017-06-04 10:52:22 130     04 June 2017      199   Manica   Manica Bandula
    ## 131 2017-06-04 11:08:13 131     04 June 2017      200   Manica   Manica Bandula
    ##               village years_farm agr_assoc  te2 X_membrs mbers_count
    ## 1                 God         11        no NULL        3           3
    ## 2                 God          2       yes NULL        7           7
    ## 3                 God         40        no NULL       10          10
    ## 4                 God          6        no NULL        7           7
    ## 5                 God         18        no NULL        7           7
    ## 6                 God          3        no NULL        3           3
    ## 7                 God         20        no NULL        6           6
    ## 8            Chirodzo         16       yes NULL       12          12
    ## 9            Chirodzo         16        no NULL        8           8
    ## 10           Chirodzo         22        no NULL       12          12
    ## 11                God          6        no NULL        6           6
    ## 12                God         20        no NULL        7           7
    ## 13                God          7       yes NULL        6           6
    ## 14                God         20       yes NULL       10          10
    ## 15                God         30       yes NULL        5           5
    ## 16                God         24       yes NULL        6           6
    ## 17                God         10       yes NULL        8           8
    ## 18                God          6        no NULL        4           4
    ## 19                God         20       yes NULL        9           9
    ## 20                God         24       yes NULL        6           6
    ## 21                God         20       yes NULL        8           8
    ## 22                God         14        no NULL        4           4
    ## 23              Ruaca         12       yes NULL       10          10
    ## 24              Ruaca          8        no NULL        6           6
    ## 25              Ruaca         10       yes NULL       11          11
    ## 26              Ruaca          2       yes NULL        3           3
    ## 27              Ruaca         36        no NULL        7           7
    ## 28              Ruaca          2        no NULL        2           2
    ## 29              Ruaca         10       yes NULL        7           7
    ## 30              Ruaca         22       yes NULL        7           7
    ## 31              Ruaca         15       yes NULL        3           3
    ## 32              Ruaca         53       yes NULL       19          19
    ## 33              Ruaca         20       yes NULL        8           8
    ## 34           Chirodzo         18       yes NULL        8           8
    ## 35           Chirodzo         45       yes NULL        5           5
    ## 36           Chirodzo         23       yes NULL        6           6
    ## 37           Chirodzo          8        no NULL        3           3
    ## 38                God         19       yes NULL       10          10
    ## 39                God         22       yes NULL        6           6
    ## 40                God         23       yes NULL        9           9
    ## 41                God         22       yes NULL        7           7
    ## 42                God          8       yes NULL        8           8
    ## 43           Chirodzo          3        no NULL        7           7
    ## 44           Chirodzo          3        no NULL        2           2
    ## 45           Chirodzo         25       yes NULL        9           9
    ## 46           Chirodzo         21       yes NULL       10          10
    ## 47           Chirodzo          2       yes NULL        2           2
    ## 48           Chirodzo         48       yes NULL        7           7
    ## 49                 49         12        no NULL        6           6
    ## 50           Chirodzo          6       yes NULL        6           6
    ## 51           Chirodzo         11       yes NULL        5           5
    ## 52           Chirodzo         15       yes NULL       11          11
    ## 53           Chirodzo         16       yes NULL        8           8
    ## 54           Chirodzo         10        no NULL        7           7
    ## 55           Chirodzo         23       yes NULL        9           9
    ## 56           Chirodzo         23       yes NULL       12          12
    ## 57           Chirodzo         20       yes NULL        4           4
    ## 58           Chirodzo         35       yes NULL       11          11
    ## 59           Chirodzo         60        no NULL        2           2
    ## 60           Chirodzo         12       yes NULL        8           8
    ## 61           Chirodzo         14       yes NULL       10          10
    ## 62           Chirodzo          5        no NULL        5           5
    ## 63           Chirodzo          1       yes NULL        4           4
    ## 64           Chirodzo          1        no NULL        6           6
    ## 65           Chirodzo         20        no NULL        8           8
    ## 66           Chirodzo         16       yes NULL       10          10
    ## 67           Chirodzo          9       yes NULL        5           5
    ## 68           Chirodzo         21       yes NULL        8           8
    ## 69           Chirodzo         12       yes NULL        4           4
    ## 70           Chirodzo         20       yes NULL        8           8
    ## 71              Ruaca         12       yes NULL        6           6
    ## 72           Chirodzo         10       yes NULL        4           4
    ## 73              Ruaca          2        no NULL        5           5
    ## 74              Ruaca         15       yes NULL       10          10
    ## 75              Ruaca         41        no NULL        5           5
    ## 76                God          5        no NULL        4           4
    ## 77              Ruaca         20       yes NULL        5           5
    ## 78                God         11       yes NULL       10          10
    ## 79              Ruaca          4        no NULL        7           7
    ## 80                God         20       yes NULL       11          11
    ## 81                God         20        no NULL        7           7
    ## 82                God         24        no NULL        7           7
    ## 83                God          1       yes NULL        5           5
    ## 84                God          7       yes NULL        5           5
    ## 85                God         21       yes NULL        7           7
    ## 86                God         11        no NULL        5           5
    ## 87                God         11        no NULL        3           3
    ## 88                God          6       yes NULL        4           4
    ## 89                God         12       yes NULL       12          12
    ## 90              Ruaca         24       yes NULL        6           6
    ## 91              Ruaca          6       yes NULL        7           7
    ## 92              Ruaca         22       yes NULL       17          17
    ## 93              Ruaca         17       yes NULL        5           5
    ## 94              Ruaca         12       yes NULL        7           7
    ## 95                God         10        no NULL        5           5
    ## 96                God         10        no NULL        3           3
    ## 97              Ruaca         50        no NULL        6           6
    ## 98              Ruaca         15       yes NULL       12          12
    ## 99              Ruaca         20        no NULL        6           6
    ## 100             Ruaca         12        no NULL        5           5
    ## 101             Ruaca         35        no NULL       14          14
    ## 102             Ruaca         20       yes NULL        6           6
    ## 103               God         22       yes NULL       15          15
    ## 104               God         12       yes NULL        4           4
    ## 105             Ruaca         22        no NULL        6           6
    ## 106             Ruaca         16        no NULL       11          11
    ## 107             Ruaca          6        no NULL        5           5
    ## 108             Ruaca          7       yes NULL        5           5
    ## 109   Ruaca-Nhamuenda         14        no NULL        3           3
    ## 110 Ruaca - Nhamuenda         16        no NULL        4           4
    ## 111               God         22        no NULL       15          15
    ## 112   Ruaca-Nhamuenda         21       yes NULL        5           5
    ## 113   Ruaca-Nhamuenda          1        no NULL       10          10
    ## 114             Ruaca          5        no NULL        7           7
    ## 115             Ruaca         24       yes NULL       10          10
    ## 116             Ruaca          8        no NULL        7           7
    ## 117               God         17       yes NULL        4           4
    ## 118               God          3       yes NULL        7           7
    ## 119             Ruaca         14        no NULL        9           9
    ## 120             Ruaca         16        no NULL       11          11
    ## 121             Ruaca         16        no NULL        8           8
    ## 122             Ruaca         13        no NULL       12          12
    ## 123             Ruaca         11        no NULL        7           7
    ## 124             Ruaca         10       yes NULL       15          15
    ## 125             Ruaca          3        no NULL       10          10
    ## 126          Chirodzo         15       yes NULL        9           9
    ## 127             Ruaca          5       yes NULL        3           3
    ## 128             Ruaca         10        no NULL        7           7
    ## 129             Ruaca          5        no NULL        4           4
    ## 130          Chirodzo         17       yes NULL        7           7
    ## 131          Chirodzo         20       yes NULL        8           8
    ##     remittance_money years_liv parents_liv sp_parents_liv grand_liv
    ## 1                 no         4          no            yes        no
    ## 2                 no         9         yes            yes       yes
    ## 3                 no        15          no             no        no
    ## 4                 no         6          no             no        no
    ## 5                 no        40         yes             no       yes
    ## 6                 no         3          no             no        no
    ## 7                 no        38         yes             no       yes
    ## 8                 no        70         yes            yes       yes
    ## 9                 no         6         yes             no       yes
    ## 10                no        23          no             no        no
    ## 11                no        20         yes            yes        no
    ## 12               yes        20          no             no        no
    ## 13                no         8         yes             no       yes
    ## 14                no        20         yes            yes        no
    ## 15                no        30         yes            yes       yes
    ## 16                no        47         yes            yes       yes
    ## 17                no        20          no             no        no
    ## 18                no        20         yes            yes        no
    ## 19                no        23         yes            yes       yes
    ## 20                no         1         yes            yes       yes
    ## 21                no        20          no            yes        no
    ## 22                no        20         yes            yes       yes
    ## 23                no        20          no             no        no
    ## 24                no         4          no             no        no
    ## 25                no         6          no             no        no
    ## 26                no        20         yes            yes       yes
    ## 27                no        36          no             no        no
    ## 28                no         2          no             no        no
    ## 29                no        10         yes             no       yes
    ## 30               yes        22          no             no        no
    ## 31                no         2         yes            yes       yes
    ## 32               yes        69         yes            yes       yes
    ## 33                no        34         yes            yes       yes
    ## 34                no        18          no             no        no
    ## 35                no        45          no             no        no
    ## 36                no        23          no             no        no
    ## 37                no         8         yes            yes        no
    ## 38               yes        19          no             no        no
    ## 39                no        22         yes            yes       yes
    ## 40               yes        23          no            yes       yes
    ## 41                no        22         yes            yes       yes
    ## 42                no         8          no             no        no
    ## 43                no        29          no             no        no
    ## 44                no         6          no             no        no
    ## 45                no         7          no             no        no
    ## 46                no        42         yes            yes       yes
    ## 47                no         2         yes            yes       yes
    ## 48                no        58         yes             no       yes
    ## 49                no        26         yes            yes       yes
    ## 50                no         7          no             no        no
    ## 51                no        30         yes             no       yes
    ## 52                no        15          no             no        no
    ## 53               yes        16         yes            yes       yes
    ## 54               yes        15         yes             no       yes
    ## 55                no        23         yes             no       yes
    ## 56                no        23         yes            yes       yes
    ## 57                no        27         yes            yes       yes
    ## 58                no        45         yes            yes       yes
    ## 59                no        60         yes            yes       yes
    ## 60                no        15         yes            yes       yes
    ## 61                no        14          no            yes       yes
    ## 62                no         5         yes             no        no
    ## 63                no        10         yes            yes        no
    ## 64                no         1          no             no        no
    ## 65                no        20          no             no        no
    ## 66                no        37         yes             no        no
    ## 67                no        31         yes             no       yes
    ## 68                no        52         yes            yes        no
    ## 69                no        12          no             no        no
    ## 70                no        25          no            yes        no
    ## 71                no        14         yes            yes       yes
    ## 72                no        18          no             no        no
    ## 73               yes        25          no             no        no
    ## 74                no        16         yes             no       yes
    ## 75                no        41         yes            yes       yes
    ## 76                no         4          no             no        no
    ## 77                no        79         yes            yes       yes
    ## 78                no        13          no             no        no
    ## 79                no        50         yes            yes       yes
    ## 80                no        25         yes             no       yes
    ## 81                no        21          no             no        no
    ## 82                no        24         yes             no       yes
    ## 83                no        43         yes             no        no
    ## 84                no        48         yes            yes        no
    ## 85                no        49         yes            yes       yes
    ## 86               yes        19         yes            yes        no
    ## 87                no        49          no             no        no
    ## 88                no         6         yes            yes       yes
    ## 89                no        12          no             no        no
    ## 90                no        24         yes            yes       yes
    ## 91                no         9         yes             no        no
    ## 92                no        48         yes            yes       yes
    ## 93                no        22          no             no        no
    ## 94                no        40         yes            yes       yes
    ## 95                no        10         yes            yes        no
    ## 96                no         4         yes            yes        no
    ## 97                no        96         yes            yes       yes
    ## 98                no        15          no             no        no
    ## 99                no        48         yes             no       yes
    ## 100               no        12          no             no        no
    ## 101               no        52         yes             no       yes
    ## 102               no        40         yes             no       yes
    ## 103               no        22          no             no        no
    ## 104               no        12         yes             no       yes
    ## 105               no        22         yes            yes       yes
    ## 106              yes        26         yes             no        no
    ## 107               no        25         yes            yes       yes
    ## 108               no        14          no            yes        no
    ## 109              yes        14         yes             no        no
    ## 110               no        16         yes            yes        no
    ## 111               no        22          no            yes        no
    ## 112               no        25          no             no        no
    ## 113               no        28         yes            yes       yes
    ## 114               no         5         yes            yes       yes
    ## 115               no        24         yes             no        no
    ## 116               no         8          no            yes        no
    ## 117               no        24         yes             no       yes
    ## 118               no        13         yes            yes       yes
    ## 119               no        14          no             no        no
    ## 120               no        16         yes            yes       yes
    ## 121               no        24         yes             no       yes
    ## 122               no        25         yes            yes       yes
    ## 123               no        36         yes            yes       yes
    ## 124               no        16          no            yes        no
    ## 125               no         5         yes             no       yes
    ## 126               no        20         yes            yes       yes
    ## 127               no         7         yes            yes       yes
    ## 128               no        10          no             no        no
    ## 129               no         5          no             no       yes
    ## 130               no        17          no             no        no
    ## 131               no        20          no            yes        no
    ##     sp_grand_liv respondent_roof_type respondent_wall_type
    ## 1            yes                grass              muddaub
    ## 2            yes                grass              muddaub
    ## 3             no        mabatisloping          burntbricks
    ## 4             no        mabatisloping          burntbricks
    ## 5             no                grass          burntbricks
    ## 6             no                grass              muddaub
    ## 7             no                grass              muddaub
    ## 8            yes        mabatisloping          burntbricks
    ## 9             no                grass          burntbricks
    ## 10            no        mabatisloping          burntbricks
    ## 11           yes                grass            sunbricks
    ## 12            no        mabatisloping          burntbricks
    ## 13            no                grass          burntbricks
    ## 14           yes                grass          burntbricks
    ## 15           yes                grass            sunbricks
    ## 16           yes                grass              muddaub
    ## 17            no                grass            sunbricks
    ## 18           yes                grass              muddaub
    ## 19           yes        mabatisloping          burntbricks
    ## 20           yes                grass          burntbricks
    ## 21           yes        mabatisloping          burntbricks
    ## 22           yes                grass              muddaub
    ## 23            no        mabatisloping          burntbricks
    ## 24            no        mabatisloping          burntbricks
    ## 25            no        mabatisloping          burntbricks
    ## 26           yes        mabatisloping          burntbricks
    ## 27            no                grass          burntbricks
    ## 28            no                grass              muddaub
    ## 29            no        mabatisloping          burntbricks
    ## 30            no                grass              muddaub
    ## 31           yes                grass              muddaub
    ## 32            no        mabatipitched              muddaub
    ## 33           yes                grass              muddaub
    ## 34            no        mabatisloping          burntbricks
    ## 35            no                grass              muddaub
    ## 36            no        mabatisloping            sunbricks
    ## 37            no        mabatisloping          burntbricks
    ## 38            no                grass              muddaub
    ## 39           yes        mabatisloping              muddaub
    ## 40           yes                grass          burntbricks
    ## 41           yes                grass              muddaub
    ## 42            no                grass            sunbricks
    ## 43            no                grass              muddaub
    ## 44            no                grass              muddaub
    ## 45            no                grass              muddaub
    ## 46           yes        mabatisloping          burntbricks
    ## 47           yes                grass              muddaub
    ## 48            no                grass              muddaub
    ## 49           yes        mabatisloping          burntbricks
    ## 50            no                grass              muddaub
    ## 51            no                grass              muddaub
    ## 52            no        mabatisloping          burntbricks
    ## 53           yes        mabatisloping          burntbricks
    ## 54            no                grass              muddaub
    ## 55            no                grass              muddaub
    ## 56           yes        mabatisloping          burntbricks
    ## 57           yes                grass          burntbricks
    ## 58           yes        mabatisloping          burntbricks
    ## 59           yes                grass              muddaub
    ## 60           yes                grass          burntbricks
    ## 61           yes                grass              muddaub
    ## 62            no                grass              muddaub
    ## 63           yes                grass              muddaub
    ## 64            no                grass              muddaub
    ## 65            no        mabatisloping          burntbricks
    ## 66            no        mabatipitched          burntbricks
    ## 67            no        mabatipitched          burntbricks
    ## 68            no        mabatipitched          burntbricks
    ## 69            no                grass              muddaub
    ## 70            no        mabatipitched          burntbricks
    ## 71           yes                grass          burntbricks
    ## 72            no                grass          burntbricks
    ## 73            no        mabatisloping          burntbricks
    ## 74            no                grass          burntbricks
    ## 75           yes                grass          burntbricks
    ## 76            no                grass          burntbricks
    ## 77            no        mabatisloping          burntbricks
    ## 78            no                grass            sunbricks
    ## 79           yes                grass              muddaub
    ## 80            no        mabatipitched            sunbricks
    ## 81            no        mabatipitched              muddaub
    ## 82            no                grass              muddaub
    ## 83           yes                grass              muddaub
    ## 84            no                grass          burntbricks
    ## 85           yes        mabatisloping          burntbricks
    ## 86            no        mabatisloping          burntbricks
    ## 87            no                grass          burntbricks
    ## 88           yes                grass              muddaub
    ## 89            no        mabatisloping          burntbricks
    ## 90           yes                grass              muddaub
    ## 91            no        mabatisloping          burntbricks
    ## 92           yes        mabatipitched          burntbricks
    ## 93            no        mabatisloping          burntbricks
    ## 94           yes                grass            sunbricks
    ## 95           yes        mabatisloping          burntbricks
    ## 96            no                grass              muddaub
    ## 97           yes        mabatisloping            sunbricks
    ## 98            no        mabatisloping          burntbricks
    ## 99            no        mabatipitched          burntbricks
    ## 100           no        mabatipitched              muddaub
    ## 101           no                grass            sunbricks
    ## 102           no        mabatisloping            sunbricks
    ## 103           no        mabatisloping            sunbricks
    ## 104           no                grass            sunbricks
    ## 105          yes        mabatisloping            sunbricks
    ## 106           no        mabatisloping          burntbricks
    ## 107           no                grass              muddaub
    ## 108          yes        mabatisloping          burntbricks
    ## 109           no                grass              muddaub
    ## 110           no        mabatisloping            sunbricks
    ## 111          yes        mabatisloping          burntbricks
    ## 112           no                grass          burntbricks
    ## 113           no                grass              muddaub
    ## 114          yes        mabatisloping          burntbricks
    ## 115           no                grass          burntbricks
    ## 116          yes                grass              muddaub
    ## 117           no                grass            sunbricks
    ## 118          yes        mabatisloping          burntbricks
    ## 119           no                grass          burntbricks
    ## 120          yes                grass              muddaub
    ## 121           no                grass              muddaub
    ## 122          yes                grass          burntbricks
    ## 123          yes        mabatisloping          burntbricks
    ## 124          yes        mabatisloping            sunbricks
    ## 125           no        mabatisloping          burntbricks
    ## 126          yes                grass          burntbricks
    ## 127          yes                grass          burntbricks
    ## 128           no        mabatisloping               cement
    ## 129           no                grass              muddaub
    ## 130           no        mabatisloping          burntbricks
    ## 131          yes        mabatisloping          burntbricks
    ##     respondent_wall_type_other respondent_floor_type window_type
    ## 1                         NULL                 earth          no
    ## 2                         NULL                 earth          no
    ## 3                         NULL                cement         yes
    ## 4                         NULL                 earth          no
    ## 5                         NULL                 earth          no
    ## 6                         NULL                 earth          no
    ## 7                         NULL                 earth          no
    ## 8                         NULL                cement          no
    ## 9                         NULL                 earth          no
    ## 10                        NULL                cement         yes
    ## 11                        NULL                 earth          no
    ## 12                        NULL                cement          no
    ## 13                        NULL                 earth          no
    ## 14                        NULL                 earth          no
    ## 15                        NULL                 earth          no
    ## 16                        NULL                 earth         yes
    ## 17                        NULL                 earth          no
    ## 18                        NULL                 earth          no
    ## 19                        NULL                 earth          no
    ## 20                        NULL                 earth         yes
    ## 21                        NULL                cement          no
    ## 22                        NULL                 earth          no
    ## 23                        NULL                cement         yes
    ## 24                        NULL                cement         yes
    ## 25                        NULL                cement          no
    ## 26                        NULL                 earth          no
    ## 27                        NULL                 earth          no
    ## 28                        NULL                 earth          no
    ## 29                        NULL                 earth          no
    ## 30                        NULL                 earth          no
    ## 31                        NULL                 earth          no
    ## 32                        NULL                 earth          no
    ## 33                        NULL                cement          no
    ## 34                        NULL                cement         yes
    ## 35                        NULL                 earth          no
    ## 36                        NULL                 earth          no
    ## 37                        NULL                 earth          no
    ## 38                        NULL                 earth          no
    ## 39                        NULL                 earth          no
    ## 40                        NULL                 earth          no
    ## 41                        NULL                 earth          no
    ## 42                        NULL                 earth         yes
    ## 43                        NULL                 earth          no
    ## 44                        NULL                 earth          no
    ## 45                        NULL                 earth          no
    ## 46                        NULL                cement          no
    ## 47                        NULL                 earth          no
    ## 48                        NULL                 earth          no
    ## 49                        NULL                 earth         yes
    ## 50                        NULL                 earth          no
    ## 51                        NULL                cement          no
    ## 52                        NULL                cement         yes
    ## 53                        NULL                cement          no
    ## 54                        NULL                 earth          no
    ## 55                        NULL                 earth          no
    ## 56                        NULL                cement          no
    ## 57                        NULL                 earth          no
    ## 58                        NULL                 earth          no
    ## 59                        NULL                 earth          no
    ## 60                        NULL                 earth          no
    ## 61                        NULL                 earth          no
    ## 62                        NULL                 earth          no
    ## 63                        NULL                 earth          no
    ## 64                        NULL                 earth          no
    ## 65                        NULL                 earth          no
    ## 66                        NULL                cement         yes
    ## 67                        NULL                cement         yes
    ## 68                        NULL                 earth          no
    ## 69                        NULL                 earth          no
    ## 70                        NULL                 earth          no
    ## 71                        NULL                 earth          no
    ## 72                        NULL                 earth          no
    ## 73                        NULL                 earth          no
    ## 74                        NULL                cement          no
    ## 75                        NULL                 earth          no
    ## 76                        NULL                 earth          no
    ## 77                        NULL                 earth          no
    ## 78                        NULL                 earth          no
    ## 79                        NULL                 earth          no
    ## 80                        NULL                 earth         yes
    ## 81                        NULL                 earth          no
    ## 82                        NULL                 earth          no
    ## 83                        NULL                 earth          no
    ## 84                        NULL                 earth          no
    ## 85                        NULL                 earth          no
    ## 86                        NULL                cement         yes
    ## 87                        NULL                 earth          no
    ## 88                        NULL                 earth          no
    ## 89                        NULL                cement          no
    ## 90                        NULL                 earth          no
    ## 91                        NULL                cement          no
    ## 92                        NULL                cement          no
    ## 93                        NULL                 earth          no
    ## 94                        NULL                 earth          no
    ## 95                        NULL                cement         yes
    ## 96                        NULL                 earth          no
    ## 97                        NULL                 earth          no
    ## 98                        NULL                 earth          no
    ## 99                        NULL                 earth          no
    ## 100                       NULL                 earth          no
    ## 101                       NULL                cement          no
    ## 102                       NULL                 earth          no
    ## 103                       NULL                cement         yes
    ## 104                       NULL                 earth          no
    ## 105                       NULL                cement          no
    ## 106                       NULL                cement          no
    ## 107                       NULL                 earth          no
    ## 108                       NULL                 earth          no
    ## 109                       NULL                 earth          no
    ## 110                       NULL                cement          no
    ## 111                       NULL                cement          no
    ## 112                       NULL                cement          no
    ## 113                       NULL                cement          no
    ## 114                       NULL                cement          no
    ## 115                       NULL                 earth          no
    ## 116                       NULL                 earth          no
    ## 117                       NULL                 earth          no
    ## 118                       NULL                 earth          no
    ## 119                       NULL                 earth          no
    ## 120                       NULL                 earth          no
    ## 121                       NULL                 earth          no
    ## 122                       NULL                cement          no
    ## 123                       NULL                 earth          no
    ## 124                       NULL                 earth          no
    ## 125                       NULL                cement         yes
    ## 126                       NULL                cement         yes
    ## 127                       NULL                 earth          no
    ## 128                       NULL                cement         yes
    ## 129                       NULL                 earth          no
    ## 130                       NULL                cement         yes
    ## 131                       NULL                cement          no
    ##     buildings_in_compound rooms other_buildings X_plots ots_count water_use
    ## 1                       1     1              no       2         2        no
    ## 2                       1     1              no       3         3       yes
    ## 3                       1     1              no       1         1        no
    ## 4                       1     1              no       3         3        no
    ## 5                       1     1              no       2         2        no
    ## 6                       1     1              no       1         1        no
    ## 7                       1     1             yes       4         4       yes
    ## 8                       2     3             yes       2         2       yes
    ## 9                       2     1             yes       3         3       yes
    ## 10                      1     5              no       2         2       yes
    ## 11                      2     1              no       2         2        no
    ## 12                      2     3              no       2         2       yes
    ## 13                      1     1              no       4         4       yes
    ## 14                      3     3              no       3         3        no
    ## 15                      1     2             yes       3         3       yes
    ## 16                      2     1             yes       1         1        no
    ## 17                      2     1              no       3         3        no
    ## 18                      1     1              no       2         2        no
    ## 19                      1     2             yes       2         2        no
    ## 20                      1     1              no       2         2        no
    ## 21                      1     1              no       4         4       yes
    ## 22                      1     1              no       1         1        no
    ## 23                      1     4             yes       2         2        no
    ## 24                      2     2             yes       3         3       yes
    ## 25                      2     3             yes       3         3       yes
    ## 26                      2     2              no       2         2       yes
    ## 27                      3     2             yes       2         2        no
    ## 28                      1     1             yes       3         3       yes
    ## 29                      1     2             yes       3         3       yes
    ## 30                      1     2              no       1         1        no
    ## 31                      7     1              no       1         1        no
    ## 32                      8     2             yes       8         8       yes
    ## 33                      2     1              no       2         2       yes
    ## 34                      2     3             yes       2         2       yes
    ## 35                      3     1              no       2         2       yes
    ## 36                      1     1              no       3         3       yes
    ## 37                      3     1              no       1         1        no
    ## 38                      3     1              no       2         2       yes
    ## 39                      1     1              no       1         1        no
    ## 40                      1     1              no       2         2       yes
    ## 41                      1     1              no       1         1        no
    ## 42                      1     1              no       2         2       yes
    ## 43                      2     1              no       4         4       yes
    ## 44                      2     1              no       1         1        no
    ## 45                      2     1              no       3         3       yes
    ## 46                      3     2              no       5         5       yes
    ## 47                      1     1             yes       2         2       yes
    ## 48                      1     1              no       1         1        no
    ## 49                      2     2              no       1         1        no
    ## 50                      1     1              no       1         1       yes
    ## 51                      1     1              no       1         1        no
    ## 52                      1     3             yes       1         1       yes
    ## 53                      2     3              no       3         3       yes
    ## 54                      3     1              no       1         1       yes
    ## 55                      2     2              no       1         1        no
    ## 56                      4     2              no       2         2       yes
    ## 57                      4     1              no       2         2       yes
    ## 58                      5     3              no       3         3       yes
    ## 59                      1     3             yes       2         2        no
    ## 60                      3     2              no       3         3       yes
    ## 61                      4     1              no       2         2       yes
    ## 62                      3     1              no       2         2        no
    ## 63                      1     1             yes       1         1        no
    ## 64                      2     1              no       2         2        no
    ## 65                      2     3              no       2         2       yes
    ## 66                      5     3             yes       1         1       yes
    ## 67                      1     2              no       1         1       yes
    ## 68                      3     3              no       3         3       yes
    ## 69                      2     1              no       1         1       yes
    ## 70                      2     2             yes       3         3       yes
    ## 71                      1     1              no       2         2       yes
    ## 72                      3     8              no       1         1        no
    ## 73                      1     2             yes       1         1       yes
    ## 74                      3     1              no       2         2       yes
    ## 75                      1     1              no       1         1        no
    ## 76                      2     1              no       2         2        no
    ## 77                      1     2             yes       3         3       yes
    ## 78                      2     1              no       2         2       yes
    ## 79                      1     1             yes       2         2       yes
    ## 80                      4     2             yes       1         1       yes
    ## 81                      2     3             yes       1         1       yes
    ## 82                      1     1              no       1         1       yes
    ## 83                      3     2             yes       2         2       yes
    ## 84                      3     1              no       3         3       yes
    ## 85                      2     2              no       2         2       yes
    ## 86                      1     2              no       2         2       yes
    ## 87                      1     1              no       2         2       yes
    ## 88                      1     2              no       2         2        no
    ## 89                      2     4             yes       2         2       yes
    ## 90                      2     1              no       3         3       yes
    ## 91                      2     2              no       3         3       yes
    ## 92                      5     2              no       6         6       yes
    ## 93                      2     1              no       2         2       yes
    ## 94                      3     1              no       3         3       yes
    ## 95                      2     2             yes       2         2       yes
    ## 96                      1     1              no       2         2       yes
    ## 97                      2     1              no       2         2       yes
    ## 98                      3     2              no       2         2       yes
    ## 99                      2     1              no       2         2       yes
    ## 100                     1     1              no       1         1       yes
    ## 101                     4     1             yes       4         4       yes
    ## 102                     2     1              no       2         2       yes
    ## 103                     4     5             yes       5         5       yes
    ## 104                     1     1             yes       3         3        no
    ## 105                     2     3             yes       3         3       yes
    ## 106                     2     3             yes       3         3       yes
    ## 107                     2     1              no       1         1        no
    ## 108                     1     1              no       3         3       yes
    ## 109                     4     1              no       2         2       yes
    ## 110                     3     2             yes       2         2        no
    ## 111                     3     2             yes       3         3       yes
    ## 112                     2     3             yes       1         1        no
    ## 113                     1     4              no       1         1        no
    ## 114                     3     4              no       2         2       yes
    ## 115                     3     2             yes       3         3       yes
    ## 116                     2     1              no       2         2       yes
    ## 117                     2     1              no       2         2       yes
    ## 118                     2     2              no       3         3       yes
    ## 119                     1     1             yes       2         2       yes
    ## 120                     2     1              no       3         3       yes
    ## 121                     5     1              no       2         2       yes
    ## 122                     2     2             yes       3         3       yes
    ## 123                     2     1              no       2         2       yes
    ## 124                     2     1             yes       3         3       yes
    ## 125                     1     4             yes       2         2       yes
    ## 126                     4     1              no       3         3       yes
    ## 127                     1     1              no       2         2       yes
    ## 128                     3     3             yes       4         4       yes
    ## 129                     2     1              no       2         2       yes
    ## 130                     1     2              no       2         2       yes
    ## 131                     1     2             yes       2         2        no
    ##     X_group_count s_group_count no_enough_water
    ## 1               2          NULL            NULL
    ## 2            NULL             3             yes
    ## 3               1          NULL            NULL
    ## 4               3          NULL            NULL
    ## 5               2          NULL            NULL
    ## 6               1          NULL            NULL
    ## 7            NULL             4             yes
    ## 8            NULL             2             yes
    ## 9            NULL             3             yes
    ## 10           NULL             2             yes
    ## 11              2          NULL            NULL
    ## 12           NULL             2             yes
    ## 13           NULL             4             yes
    ## 14              3          NULL            NULL
    ## 15           NULL             3             yes
    ## 16              1          NULL            NULL
    ## 17              3          NULL            NULL
    ## 18              2          NULL            NULL
    ## 19              2          NULL            NULL
    ## 20              2          NULL            NULL
    ## 21           NULL             4             yes
    ## 22              1          NULL            NULL
    ## 23              2          NULL            NULL
    ## 24           NULL             3             yes
    ## 25           NULL             3             yes
    ## 26           NULL             2             yes
    ## 27              2          NULL            NULL
    ## 28           NULL             3             yes
    ## 29           NULL             3             yes
    ## 30              1          NULL            NULL
    ## 31              1          NULL            NULL
    ## 32           NULL             8             yes
    ## 33           NULL             2             yes
    ## 34           NULL             2             yes
    ## 35           NULL             2             yes
    ## 36           NULL             3              no
    ## 37              1          NULL            NULL
    ## 38           NULL             2             yes
    ## 39              1          NULL            NULL
    ## 40           NULL             2             yes
    ## 41              1          NULL            NULL
    ## 42           NULL             2             yes
    ## 43           NULL             4              no
    ## 44              1          NULL            NULL
    ## 45           NULL             3             yes
    ## 46           NULL             5             yes
    ## 47           NULL             2             yes
    ## 48              1          NULL            NULL
    ## 49              1          NULL            NULL
    ## 50           NULL             1             yes
    ## 51              1          NULL            NULL
    ## 52           NULL             1             yes
    ## 53           NULL             3             yes
    ## 54           NULL             1             yes
    ## 55              1          NULL            NULL
    ## 56           NULL             2             yes
    ## 57           NULL             2              no
    ## 58           NULL             3              no
    ## 59              2          NULL            NULL
    ## 60           NULL             3             yes
    ## 61           NULL             2             yes
    ## 62              2          NULL            NULL
    ## 63              1          NULL            NULL
    ## 64              2          NULL            NULL
    ## 65           NULL             2             yes
    ## 66           NULL             1             yes
    ## 67           NULL             1             yes
    ## 68           NULL             3             yes
    ## 69           NULL             1             yes
    ## 70           NULL             3             yes
    ## 71           NULL             2             yes
    ## 72              1          NULL            NULL
    ## 73           NULL             1             yes
    ## 74           NULL             2             yes
    ## 75              1          NULL            NULL
    ## 76              2          NULL            NULL
    ## 77           NULL             3             yes
    ## 78           NULL             2             yes
    ## 79           NULL             2             yes
    ## 80           NULL             1             yes
    ## 81           NULL             1             yes
    ## 82           NULL             1             yes
    ## 83           NULL             2             yes
    ## 84           NULL             3             yes
    ## 85           NULL             2             yes
    ## 86           NULL             2             yes
    ## 87           NULL             2             yes
    ## 88              2          NULL            NULL
    ## 89           NULL             2             yes
    ## 90           NULL             3             yes
    ## 91           NULL             3             yes
    ## 92           NULL             6             yes
    ## 93           NULL             2             yes
    ## 94           NULL             3             yes
    ## 95           NULL             2             yes
    ## 96           NULL             2             yes
    ## 97           NULL             2             yes
    ## 98           NULL             2             yes
    ## 99           NULL             2             yes
    ## 100          NULL             1             yes
    ## 101          NULL             4             yes
    ## 102          NULL             2             yes
    ## 103          NULL             5             yes
    ## 104             3          NULL            NULL
    ## 105          NULL             3             yes
    ## 106          NULL             3             yes
    ## 107             1          NULL            NULL
    ## 108          NULL             3             yes
    ## 109          NULL             2              no
    ## 110             2          NULL            NULL
    ## 111          NULL             3             yes
    ## 112             1          NULL            NULL
    ## 113             1          NULL            NULL
    ## 114          NULL             2             yes
    ## 115          NULL             3             yes
    ## 116          NULL             2             yes
    ## 117          NULL             2              no
    ## 118          NULL             3             yes
    ## 119          NULL             2             yes
    ## 120          NULL             3             yes
    ## 121          NULL             2             yes
    ## 122          NULL             3             yes
    ## 123          NULL             2             yes
    ## 124          NULL             3             yes
    ## 125          NULL             2             yes
    ## 126          NULL             3             yes
    ## 127          NULL             2             yes
    ## 128          NULL             4             yes
    ## 129          NULL             2             yes
    ## 130          NULL             2             yes
    ## 131             2          NULL            NULL
    ##                                                               months_no_water
    ## 1                                                                        NULL
    ## 2                                                           ['Aug' ;  'Sept']
    ## 3                                                                        NULL
    ## 4                                                                        NULL
    ## 5                                                                        NULL
    ## 6                                                                        NULL
    ## 7                                                  ['Aug' ;  'Sept' ;  'Oct']
    ## 8                                                           ['Sept' ;  'Oct']
    ## 9                                                            ['Oct' ;  'Nov']
    ## 10                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 11                                                                       NULL
    ## 12                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 13                                                                    ['Oct']
    ## 14                                                                       NULL
    ## 15                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 16                                                                       NULL
    ## 17                                                                       NULL
    ## 18                                                                       NULL
    ## 19                                                                       NULL
    ## 20                                                                       NULL
    ## 21                                                                    ['Oct']
    ## 22                                                                       NULL
    ## 23                                                                       NULL
    ## 24                                                          ['Sept' ;  'Oct']
    ## 25                                                          ['Aug' ;  'Sept']
    ## 26                                                           ['Oct' ;  'Nov']
    ## 27                                                                       NULL
    ## 28                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 29                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 30                                                                       NULL
    ## 31                                                                       NULL
    ## 32                                                          ['Sept' ;  'Oct']
    ## 33                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 34                                                           ['Oct' ;  'Nov']
    ## 35                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 36                                                                       NULL
    ## 37                                                                       NULL
    ## 38                                                          ['Sept' ;  'Oct']
    ## 39                                                                       NULL
    ## 40                                                          ['Sept' ;  'Oct']
    ## 41                                                                       NULL
    ## 42                                                          ['Aug' ;  'Sept']
    ## 43                                                                       NULL
    ## 44                                                                       NULL
    ## 45                                                          ['Sept' ;  'Oct']
    ## 46                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 47                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 48                                                                       NULL
    ## 49                                                                       NULL
    ## 50                                                          ['Sept' ;  'Oct']
    ## 51                                                                       NULL
    ## 52                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 53                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 54                               ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 55                                                                       NULL
    ## 56                                                          ['Sept' ;  'Oct']
    ## 57                                                                       NULL
    ## 58                                                                       NULL
    ## 59                                                                       NULL
    ## 60                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 61                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 62                                                                       NULL
    ## 63                                                                       NULL
    ## 64                                                                       NULL
    ## 65                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 66                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 67                                                           ['Oct' ;  'Nov']
    ## 68                                                           ['Nov' ;  'Dec']
    ## 69                                                           ['Nov' ;  'Dec']
    ## 70                                                          ['Aug' ;  'Sept']
    ## 71                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 72                                                                       NULL
    ## 73                                                                    ['Nov']
    ## 74                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 75                                                                       NULL
    ## 76                                                                       NULL
    ## 77                                                           ['Oct' ;  'Nov']
    ## 78                                                           ['Oct' ;  'Nov']
    ## 79                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 80                                                          ['Sept' ;  'Oct']
    ## 81                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 82                                                          ['Sept' ;  'Oct']
    ## 83                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 84                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 85                                                           ['Oct' ;  'Nov']
    ## 86                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 87                                                           ['Jan' ;  'Dec']
    ## 88                                                                       NULL
    ## 89                               ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 90                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 91                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 92                                                          ['Sept' ;  'Oct']
    ## 93                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 94                                                          ['Sept' ;  'Oct']
    ## 95                                                          ['Sept' ;  'Oct']
    ## 96                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 97                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 98                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 99                                                          ['Aug' ;  'Sept']
    ## 100                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 101                                                         ['Aug' ;  'Sept']
    ## 102                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 103                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 104                                                                      NULL
    ## 105                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 106                                                         ['Sept' ;  'Oct']
    ## 107                                                                      NULL
    ## 108                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 109                                                                      NULL
    ## 110                                                                      NULL
    ## 111                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 112                                                                      NULL
    ## 113                                                                      NULL
    ## 114                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 115                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 116 ['Apr' ;  'May' ;  'June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 117                                                                      NULL
    ## 118                                                          ['Jan' ;  'Dec']
    ## 119                              ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 120                                                ['Aug' ;  'Sept' ;  'Oct']
    ## 121                    ['July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 122                                       ['Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 123                                                          ['Oct' ;  'Nov']
    ## 124                              ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 125                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 126                                                         ['Sept' ;  'Nov']
    ## 127                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 128                                                 ['Oct' ;  'Nov' ;  'Dec']
    ## 129                                                ['Aug' ;  'Sept' ;  'Oct']
    ## 130                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 131                                                                      NULL
    ##     period_use exper_other other_meth
    ## 1         NULL        NULL       NULL
    ## 2            2         yes         no
    ## 3         NULL        NULL       NULL
    ## 4         NULL        NULL       NULL
    ## 5         NULL        NULL       NULL
    ## 6         NULL        NULL       NULL
    ## 7           10         yes         no
    ## 8           10         yes         no
    ## 9            6         yes         no
    ## 10          22         yes         no
    ## 11        NULL        NULL       NULL
    ## 12          20         yes         no
    ## 13           7         yes         no
    ## 14        NULL        NULL       NULL
    ## 15          30         yes         no
    ## 16        NULL        NULL       NULL
    ## 17        NULL        NULL       NULL
    ## 18        NULL        NULL       NULL
    ## 19        NULL        NULL       NULL
    ## 20        NULL        NULL       NULL
    ## 21          20         yes         no
    ## 22        NULL        NULL       NULL
    ## 23        NULL        NULL       NULL
    ## 24           8         yes         no
    ## 25          10         yes         no
    ## 26           2         yes         no
    ## 27        NULL        NULL       NULL
    ## 28           2         yes         no
    ## 29           4         yes        yes
    ## 30        NULL        NULL       NULL
    ## 31        NULL        NULL       NULL
    ## 32          45         yes         no
    ## 33          20         yes         no
    ## 34           2         yes         no
    ## 35          20         yes         no
    ## 36          23         yes         no
    ## 37        NULL        NULL       NULL
    ## 38           9         yes         no
    ## 39        NULL        NULL       NULL
    ## 40          23         yes         no
    ## 41        NULL        NULL       NULL
    ## 42           5         yes         no
    ## 43           3         yes         no
    ## 44        NULL        NULL       NULL
    ## 45          20         yes         no
    ## 46          21         yes         no
    ## 47           2         yes         no
    ## 48        NULL        NULL       NULL
    ## 49        NULL        NULL       NULL
    ## 50           1          no         no
    ## 51        NULL        NULL       NULL
    ## 52          15          no         no
    ## 53          16         yes         no
    ## 54          10         yes         no
    ## 55        NULL        NULL       NULL
    ## 56          23         yes         no
    ## 57          20         yes         no
    ## 58          35         yes         no
    ## 59        NULL        NULL       NULL
    ## 60          12         yes         no
    ## 61          13         yes         no
    ## 62        NULL        NULL       NULL
    ## 63        NULL        NULL       NULL
    ## 64        NULL        NULL       NULL
    ## 65          20         yes         no
    ## 66          10          no         no
    ## 67           9         yes         no
    ## 68          21         yes         no
    ## 69          12         yes         no
    ## 70          20         yes         no
    ## 71           1         yes         no
    ## 72        NULL        NULL       NULL
    ## 73           2         yes         no
    ## 74          16         yes         no
    ## 75        NULL        NULL       NULL
    ## 76        NULL        NULL       NULL
    ## 77          20         yes         no
    ## 78          11          no         no
    ## 79           4         yes         no
    ## 80          23         yes         no
    ## 81          20         yes         no
    ## 82          21         yes         no
    ## 83          24         yes         no
    ## 84           5         yes         no
    ## 85          21         yes         no
    ## 86          11         yes         no
    ## 87          11         yes         no
    ## 88        NULL        NULL       NULL
    ## 89           9         yes         no
    ## 90           4         yes         no
    ## 91           4         yes        yes
    ## 92          22         yes         no
    ## 93          17         yes         no
    ## 94          12         yes         no
    ## 95          10          no         no
    ## 96          10         yes         no
    ## 97          10         yes         no
    ## 98           2         yes         no
    ## 99          20         yes         no
    ## 100         12         yes         no
    ## 101         16         yes         no
    ## 102          1         yes         no
    ## 103         21         yes         no
    ## 104       NULL        NULL       NULL
    ## 105         22         yes         no
    ## 106          2         yes         no
    ## 107       NULL        NULL       NULL
    ## 108          3         yes        yes
    ## 109          3         yes         no
    ## 110       NULL        NULL       NULL
    ## 111         16         yes         no
    ## 112       NULL        NULL       NULL
    ## 113       NULL        NULL       NULL
    ## 114          5         yes         no
    ## 115         12         yes         no
    ## 116          8         yes         no
    ## 117          2         yes         no
    ## 118          3         yes         no
    ## 119         10         yes         no
    ## 120          2         yes         no
    ## 121         16         yes         no
    ## 122         13         yes        yes
    ## 123         11         yes         no
    ## 124          7         yes         no
    ## 125          3         yes         no
    ## 126          5         yes         no
    ## 127          4         yes         no
    ## 128         10         yes         no
    ## 129          2         yes         no
    ## 130          6         yes         no
    ## 131       NULL        NULL       NULL
    ##                                            res_change memb_assoc resp_assoc
    ## 1                                                NULL       NULL       NULL
    ## 2                                                NULL        yes         no
    ## 3                                                NULL       NULL       NULL
    ## 4                                                NULL       NULL       NULL
    ## 5                                                NULL       NULL       NULL
    ## 6                                                NULL       NULL       NULL
    ## 7                                                NULL         no       NULL
    ## 8                                                NULL        yes        yes
    ## 9                                                NULL         no       NULL
    ## 10                                               NULL         no       NULL
    ## 11                                               NULL       NULL       NULL
    ## 12                                               NULL        yes         no
    ## 13                                               NULL         no       NULL
    ## 14                                               NULL       NULL       NULL
    ## 15                                               NULL        yes         no
    ## 16                                               NULL       NULL       NULL
    ## 17                                               NULL       NULL       NULL
    ## 18                                               NULL       NULL       NULL
    ## 19                                               NULL       NULL       NULL
    ## 20                                               NULL       NULL       NULL
    ## 21                                               NULL         no       NULL
    ## 22                                               NULL       NULL       NULL
    ## 23                                               NULL       NULL       NULL
    ## 24                                               NULL         no       NULL
    ## 25                                               NULL         no       NULL
    ## 26                                               NULL         no       NULL
    ## 27                                               NULL       NULL       NULL
    ## 28                                               NULL         no       NULL
    ## 29                                      ['less_work']        yes        yes
    ## 30                                               NULL       NULL       NULL
    ## 31                                               NULL       NULL       NULL
    ## 32                                               NULL        yes         no
    ## 33                                               NULL         no       NULL
    ## 34                                               NULL        yes         no
    ## 35                                               NULL        yes         no
    ## 36                                               NULL        yes         no
    ## 37                                               NULL       NULL       NULL
    ## 38                                               NULL        yes         no
    ## 39                                               NULL       NULL       NULL
    ## 40                                               NULL        yes         no
    ## 41                                               NULL       NULL       NULL
    ## 42                                               NULL         no       NULL
    ## 43                                               NULL         no       NULL
    ## 44                                               NULL       NULL       NULL
    ## 45                                               NULL         no       NULL
    ## 46                                               NULL         no       NULL
    ## 47                                               NULL        yes         no
    ## 48                                               NULL       NULL       NULL
    ## 49                                               NULL       NULL       NULL
    ## 50                                               NULL        yes         no
    ## 51                                               NULL       NULL       NULL
    ## 52                                               NULL         no       NULL
    ## 53                                               NULL        yes         no
    ## 54                                               NULL         no       NULL
    ## 55                                               NULL       NULL       NULL
    ## 56                                               NULL        yes         no
    ## 57                                               NULL         no       NULL
    ## 58                                               NULL         no       NULL
    ## 59                                               NULL       NULL       NULL
    ## 60                                               NULL         no       NULL
    ## 61                                               NULL        yes        yes
    ## 62                                               NULL       NULL       NULL
    ## 63                                               NULL       NULL       NULL
    ## 64                                               NULL       NULL       NULL
    ## 65                                               NULL         no       NULL
    ## 66                                               NULL        yes         no
    ## 67                                               NULL         no       NULL
    ## 68                                               NULL         no       NULL
    ## 69                                               NULL         no       NULL
    ## 70                                               NULL         no       NULL
    ## 71                                               NULL        yes         no
    ## 72                                               NULL       NULL       NULL
    ## 73                                               NULL         no       NULL
    ## 74                                               NULL        yes         no
    ## 75                                               NULL       NULL       NULL
    ## 76                                               NULL       NULL       NULL
    ## 77                                               NULL        yes        yes
    ## 78                                               NULL         no       NULL
    ## 79                                               NULL         no       NULL
    ## 80                                               NULL        yes         no
    ## 81                                               NULL         no       NULL
    ## 82                                               NULL         no       NULL
    ## 83                                               NULL        yes         no
    ## 84                                               NULL         no       NULL
    ## 85                                               NULL        yes         no
    ## 86                                               NULL         no       NULL
    ## 87                                               NULL         no       NULL
    ## 88                                               NULL       NULL       NULL
    ## 89                                               NULL        yes         no
    ## 90                                               NULL        yes        yes
    ## 91  ['cheaper' ;  'less_work' ;  'train_outside_org']        yes         no
    ## 92                                               NULL        yes        yes
    ## 93                                               NULL        yes         no
    ## 94                                               NULL         no       NULL
    ## 95                                               NULL         no       NULL
    ## 96                                               NULL         no       NULL
    ## 97                                               NULL         no       NULL
    ## 98                                               NULL        yes        yes
    ## 99                                               NULL         no       NULL
    ## 100                                              NULL         no       NULL
    ## 101                                              NULL        yes         no
    ## 102                                              NULL        yes        yes
    ## 103                                              NULL         no       NULL
    ## 104                                              NULL       NULL       NULL
    ## 105                                              NULL         no       NULL
    ## 106                                              NULL         no       NULL
    ## 107                                              NULL       NULL       NULL
    ## 108                                     ['less_work']         no       NULL
    ## 109                                              NULL         no       NULL
    ## 110                                              NULL       NULL       NULL
    ## 111                                              NULL         no       NULL
    ## 112                                              NULL       NULL       NULL
    ## 113                                              NULL       NULL       NULL
    ## 114                                              NULL         no       NULL
    ## 115                                              NULL         no       NULL
    ## 116                                              NULL         no       NULL
    ## 117                                              NULL         no       NULL
    ## 118                                              NULL        yes        yes
    ## 119                                              NULL         no       NULL
    ## 120                                              NULL         no       NULL
    ## 121                                              NULL         no       NULL
    ## 122                                       ['cheaper']         no       NULL
    ## 123                                              NULL         no       NULL
    ## 124                                              NULL         no       NULL
    ## 125                                              NULL         no       NULL
    ## 126                                              NULL         no       NULL
    ## 127                                              NULL         no       NULL
    ## 128                                              NULL         no       NULL
    ## 129                                              NULL         no       NULL
    ## 130                                              NULL        yes        yes
    ## 131                                              NULL       NULL       NULL
    ##     fees_water affect_conflicts   te need_money                    money_source
    ## 1         NULL             NULL NULL       NULL                            NULL
    ## 2           no             once NULL         no                            NULL
    ## 3         NULL             NULL NULL       NULL                            NULL
    ## 4         NULL             NULL NULL       NULL                            NULL
    ## 5         NULL             NULL NULL       NULL                            NULL
    ## 6         NULL             NULL NULL       NULL                            NULL
    ## 7           no            never NULL         no                            NULL
    ## 8           no            never NULL         no                            NULL
    ## 9           no            never NULL         no                            NULL
    ## 10          no            never NULL         no                            NULL
    ## 11        NULL             NULL NULL       NULL                            NULL
    ## 12          no            never NULL         no                            NULL
    ## 13          no            never NULL         no                            NULL
    ## 14        NULL             NULL NULL       NULL                            NULL
    ## 15          no             once NULL         no                            NULL
    ## 16        NULL             NULL NULL       NULL                            NULL
    ## 17        NULL             NULL NULL       NULL                            NULL
    ## 18        NULL             NULL NULL       NULL                            NULL
    ## 19        NULL             NULL NULL       NULL                            NULL
    ## 20        NULL             NULL NULL       NULL                            NULL
    ## 21          no            never NULL         no                            NULL
    ## 22        NULL             NULL NULL       NULL                            NULL
    ## 23        NULL             NULL NULL       NULL                            NULL
    ## 24          no            never NULL         no                            NULL
    ## 25          no            never NULL        yes ['business' ;  'non_farm_prod']
    ## 26          no            never NULL         no                            NULL
    ## 27        NULL             NULL NULL       NULL                            NULL
    ## 28          no        more_once NULL         no                            NULL
    ## 29          no       frequently NULL         no                            NULL
    ## 30        NULL             NULL NULL       NULL                            NULL
    ## 31        NULL             NULL NULL       NULL                            NULL
    ## 32          no        more_once NULL        yes                     ['farming']
    ## 33          no        more_once NULL         no                            NULL
    ## 34          no        more_once NULL         no                            NULL
    ## 35          no        more_once NULL         no                            NULL
    ## 36          no             once NULL         no                            NULL
    ## 37        NULL             NULL NULL       NULL                            NULL
    ## 38          no            never NULL         no                            NULL
    ## 39        NULL             NULL NULL       NULL                            NULL
    ## 40          no            never NULL         no                            NULL
    ## 41        NULL             NULL NULL       NULL                            NULL
    ## 42          no            never NULL         no                            NULL
    ## 43          no            never NULL         no                            NULL
    ## 44        NULL             NULL NULL       NULL                            NULL
    ## 45          no            never NULL        yes  ['farming' ;  'non_farm_prod']
    ## 46          no             once NULL         no                            NULL
    ## 47          no             once NULL         no                            NULL
    ## 48        NULL             NULL NULL       NULL                            NULL
    ## 49        NULL             NULL NULL       NULL                            NULL
    ## 50          no            never NULL         no                            NULL
    ## 51        NULL             NULL NULL       NULL                            NULL
    ## 52          no            never NULL         no                            NULL
    ## 53          no       frequently NULL         no                            NULL
    ## 54          no            never NULL         no                            NULL
    ## 55        NULL             NULL NULL       NULL                            NULL
    ## 56          no            never NULL         no                            NULL
    ## 57          no            never NULL         no                            NULL
    ## 58          no            never NULL         no                            NULL
    ## 59        NULL             NULL NULL       NULL                            NULL
    ## 60          no            never NULL         no                            NULL
    ## 61          no        more_once NULL         no                            NULL
    ## 62        NULL             NULL NULL       NULL                            NULL
    ## 63        NULL             NULL NULL       NULL                            NULL
    ## 64        NULL             NULL NULL       NULL                            NULL
    ## 65          no             once NULL         no                            NULL
    ## 66          no       frequently NULL         no                            NULL
    ## 67          no        more_once NULL         no                            NULL
    ## 68          no        more_once NULL         no                            NULL
    ## 69          no        more_once NULL         no                            NULL
    ## 70          no        more_once NULL         no                            NULL
    ## 71          no        more_once NULL         no                            NULL
    ## 72        NULL             NULL NULL       NULL                            NULL
    ## 73          no            never NULL         no                            NULL
    ## 74          no             once NULL         no                            NULL
    ## 75        NULL             NULL NULL       NULL                            NULL
    ## 76        NULL             NULL NULL       NULL                            NULL
    ## 77          no       frequently NULL         no                            NULL
    ## 78          no        more_once NULL         no                            NULL
    ## 79          no            never NULL         no                            NULL
    ## 80          no        more_once NULL         no                            NULL
    ## 81          no        more_once NULL         no                            NULL
    ## 82          no        more_once NULL         no                            NULL
    ## 83          no        more_once NULL         no                            NULL
    ## 84          no            never NULL         no                            NULL
    ## 85          no        more_once NULL         no                            NULL
    ## 86          no        more_once NULL         no                            NULL
    ## 87          no            never NULL         no                            NULL
    ## 88        NULL             NULL NULL       NULL                            NULL
    ## 89          no        more_once NULL         no                            NULL
    ## 90          no        more_once NULL         no                            NULL
    ## 91          no        more_once NULL         no                            NULL
    ## 92          no        more_once NULL         no                            NULL
    ## 93          no            never NULL         no                            NULL
    ## 94          no            never NULL         no                            NULL
    ## 95          no            never NULL         no                            NULL
    ## 96          no            never NULL         no                            NULL
    ## 97          no            never NULL         no                            NULL
    ## 98          no       frequently NULL         no                            NULL
    ## 99          no        more_once NULL         no                            NULL
    ## 100         no        more_once NULL         no                            NULL
    ## 101         no            never NULL         no                            NULL
    ## 102         no       frequently NULL         no                            NULL
    ## 103         no            never NULL         no                            NULL
    ## 104       NULL             NULL NULL       NULL                            NULL
    ## 105         no            never NULL         no                            NULL
    ## 106         no            never NULL         no                            NULL
    ## 107       NULL             NULL NULL       NULL                            NULL
    ## 108         no        more_once NULL         no                            NULL
    ## 109         no            never NULL         no                            NULL
    ## 110       NULL             NULL NULL       NULL                            NULL
    ## 111         no            never NULL         no                            NULL
    ## 112       NULL             NULL NULL       NULL                            NULL
    ## 113       NULL             NULL NULL       NULL                            NULL
    ## 114        yes       frequently NULL        yes                     ['farming']
    ## 115         no       frequently NULL         no                            NULL
    ## 116         no            never NULL         no                            NULL
    ## 117         no            never NULL         no                            NULL
    ## 118         no       frequently NULL         no                            NULL
    ## 119         no            never NULL         no                            NULL
    ## 120         no            never NULL         no                            NULL
    ## 121         no            never NULL         no                            NULL
    ## 122         no            never NULL         no                            NULL
    ## 123         no            never NULL         no                            NULL
    ## 124         no            never NULL         no                            NULL
    ## 125         no            never NULL         no                            NULL
    ## 126         no             once NULL         no                            NULL
    ## 127         no        more_once NULL         no                            NULL
    ## 128         no        more_once NULL         no                            NULL
    ## 129         no        more_once NULL         no                            NULL
    ## 130         no        more_once NULL        yes       ['farming' ;  'business']
    ## 131       NULL             NULL NULL       NULL                            NULL
    ##     money_source_other crops_contr emply_lab du_labour
    ## 1                 NULL        NULL        no        no
    ## 2                 NULL   more_half       yes        no
    ## 3                 NULL        NULL        no       yes
    ## 4                 NULL        NULL        no       yes
    ## 5                 NULL        NULL        no        no
    ## 6                 NULL        NULL        no       yes
    ## 7                 NULL   more_half        no        no
    ## 8                 NULL    abt_half       yes        no
    ## 9                 NULL   more_half       yes       yes
    ## 10                NULL   more_half       yes        no
    ## 11                NULL        NULL        no       yes
    ## 12                NULL   more_half        no        no
    ## 13                NULL   more_half       yes        no
    ## 14                NULL        NULL       yes       yes
    ## 15                NULL    abt_half        no        no
    ## 16                NULL        NULL       yes       yes
    ## 17                NULL        NULL        no       yes
    ## 18                NULL        NULL        no       yes
    ## 19                NULL        NULL       yes       yes
    ## 20                NULL        NULL        no       yes
    ## 21                NULL   less_half        no       yes
    ## 22                NULL        NULL        no       yes
    ## 23                NULL        NULL       yes        no
    ## 24                NULL   less_half       yes        no
    ## 25                NULL   more_half       yes        no
    ## 26                NULL    abt_half       yes       yes
    ## 27                NULL        NULL        no        no
    ## 28                NULL   more_half        no       yes
    ## 29                NULL   more_half        no        no
    ## 30                NULL        NULL        no       yes
    ## 31                NULL        NULL        no        no
    ## 32                NULL   more_half       yes       yes
    ## 33                NULL   more_half        no        no
    ## 34                NULL   more_half        no        no
    ## 35                NULL   more_half        no       yes
    ## 36                NULL    abt_half       yes       yes
    ## 37                NULL        NULL        no        no
    ## 38                NULL   more_half        no       yes
    ## 39                NULL        NULL        no        no
    ## 40                NULL   more_half        no        no
    ## 41                NULL        NULL        no        no
    ## 42                NULL   less_half        no        no
    ## 43                NULL    abt_half       yes        no
    ## 44                NULL        NULL       yes        no
    ## 45                NULL   more_half       yes        no
    ## 46                NULL   more_half       yes        no
    ## 47                NULL   more_half        no        no
    ## 48                NULL        NULL        no        no
    ## 49                NULL        NULL        no       yes
    ## 50                NULL    abt_half       yes        no
    ## 51                NULL        NULL        no       yes
    ## 52                NULL   less_half        no        no
    ## 53                NULL   more_half        no        no
    ## 54                NULL   more_half        no        no
    ## 55                NULL        NULL        no        no
    ## 56                NULL   more_half        no        no
    ## 57                NULL   less_half        no        no
    ## 58                NULL   more_half        no        no
    ## 59                NULL        NULL        no        no
    ## 60                NULL   more_half       yes       yes
    ## 61                NULL   more_half       yes        no
    ## 62                NULL        NULL        no       yes
    ## 63                NULL        NULL        no       yes
    ## 64                NULL        NULL        no        no
    ## 65                NULL    abt_half        no        no
    ## 66                NULL   more_half       yes        no
    ## 67                NULL   more_half       yes       yes
    ## 68                NULL   more_half        no        no
    ## 69                NULL   more_half        no        no
    ## 70                NULL   more_half        no       yes
    ## 71                NULL   more_half        no       yes
    ## 72                NULL        NULL        no        no
    ## 73                NULL    abt_half        no       yes
    ## 74                NULL    abt_half        no        no
    ## 75                NULL        NULL        no       yes
    ## 76                NULL        NULL       yes        no
    ## 77                NULL    abt_half       yes       yes
    ## 78                NULL   more_half       yes        no
    ## 79                NULL    abt_half        no       yes
    ## 80                NULL   more_half        no        no
    ## 81                NULL   more_half        no        no
    ## 82                NULL   more_half        no        no
    ## 83                NULL   more_half        no        no
    ## 84                NULL   more_half       yes        no
    ## 85                NULL   more_half        no        no
    ## 86                NULL   more_half       yes        no
    ## 87                NULL   less_half       yes        no
    ## 88                NULL        NULL        no       yes
    ## 89                NULL   more_half        no       yes
    ## 90                NULL   more_half        no       yes
    ## 91                NULL   more_half       yes        no
    ## 92                NULL   more_half        no        no
    ## 93                NULL    abt_half        no        no
    ## 94                NULL    abt_half       yes       yes
    ## 95                NULL   less_half        no       yes
    ## 96                NULL    abt_half        no       yes
    ## 97                NULL   less_half       yes        no
    ## 98                NULL   less_half        no       yes
    ## 99                NULL    abt_half        no        no
    ## 100               NULL   more_half        no       yes
    ## 101               NULL    abt_half        no        no
    ## 102               NULL   more_half        no       yes
    ## 103               NULL   more_half       yes        no
    ## 104               NULL        NULL        no        no
    ## 105               NULL    abt_half        no        no
    ## 106               NULL   less_half       yes        no
    ## 107               NULL        NULL        no       yes
    ## 108               NULL   less_half       yes       yes
    ## 109               NULL   more_half        no        no
    ## 110               NULL        NULL       yes        no
    ## 111               NULL    abt_half        no        no
    ## 112               NULL        NULL        no       yes
    ## 113               NULL        NULL        no       yes
    ## 114               NULL    abt_half        no        no
    ## 115               NULL   more_half       yes        no
    ## 116               NULL   less_half        no       yes
    ## 117               NULL   less_half        no       yes
    ## 118               NULL   more_half       yes       yes
    ## 119               NULL   less_half        no        no
    ## 120               NULL   less_half        no       yes
    ## 121               NULL   less_half        no       yes
    ## 122               NULL   more_half       yes        no
    ## 123               NULL   more_half        no        no
    ## 124               NULL   more_half        no       yes
    ## 125               NULL    abt_half        no        no
    ## 126               NULL   more_half       yes       yes
    ## 127               NULL   less_half       yes       yes
    ## 128               NULL   more_half        no       yes
    ## 129               NULL   more_half        no       yes
    ## 130               NULL   more_half       yes        no
    ## 131               NULL        NULL        no       yes
    ##                                                 liv_owned liv_owned_other
    ## 1                                             ['poultry']            NULL
    ## 2                           ['oxen' ;  'cows' ;  'goats']            NULL
    ## 3                                                ['none']            NULL
    ## 4                                      ['oxen' ;  'cows']            NULL
    ## 5              ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 6                                                ['none']            NULL
    ## 7                                                ['oxen']            NULL
    ## 8                                     ['oxen' ;  'goats']            NULL
    ## 9                           ['oxen' ;  'cows' ;  'goats']            NULL
    ## 10                                     ['oxen' ;  'cows']            NULL
    ## 11                                     ['oxen' ;  'cows']            NULL
    ## 12                                     ['oxen' ;  'cows']            NULL
    ## 13                       ['cows' ;  'goats' ;  'poultry']            NULL
    ## 14                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 15                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 16             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 17                                              ['goats']            NULL
    ## 18                       ['goats' ;  'pigs' ;  'poultry']            NULL
    ## 19                                    ['oxen' ;  'goats']            NULL
    ## 20                                               ['cows']            NULL
    ## 21                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 22                                              ['goats']            NULL
    ## 23                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 24                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 25                                     ['oxen' ;  'cows']            NULL
    ## 26                                     ['oxen' ;  'cows']            NULL
    ## 27                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 28                                               ['none']            NULL
    ## 29                                              ['goats']            NULL
    ## 30                                               ['none']            NULL
    ## 31                                               ['none']            NULL
    ## 32   ['oxen' ;  'cows' ;  'goats' ;  'pigs' ;  'poultry']            NULL
    ## 33                                  ['oxen' ;  'poultry']            NULL
    ## 34                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 35                                     ['oxen' ;  'cows']            NULL
    ## 36                           ['oxen' ;  'cows' ;  'pigs']            NULL
    ## 37                                     ['oxen' ;  'cows']            NULL
    ## 38                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 39                                               ['oxen']            NULL
    ## 40                                               ['oxen']            NULL
    ## 41                                  ['oxen' ;  'poultry']            NULL
    ## 42                       ['cows' ;  'goats' ;  'poultry']            NULL
    ## 43                                     ['oxen' ;  'cows']            NULL
    ## 44                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 45             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 46                                  ['oxen' ;  'poultry']            NULL
    ## 47                                               ['none']            NULL
    ## 48                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 49                                 ['goats' ;  'poultry']            NULL
    ## 50                                            ['poultry']            NULL
    ## 51                                            ['poultry']            NULL
    ## 52                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 53                                    ['oxen' ;  'goats']            NULL
    ## 54                                               ['none']            NULL
    ## 55                                              ['goats']            NULL
    ## 56                                    ['oxen' ;  'goats']            NULL
    ## 57                                               ['none']            NULL
    ## 58                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 59                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 60             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 61                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 62                                               ['none']            NULL
    ## 63                                               ['none']            NULL
    ## 64                                              ['goats']            NULL
    ## 65                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 66             ['oxen' ;  'cows' ;  'goats' ;  'donkeys']            NULL
    ## 67             ['oxen' ;  'cows' ;  'goats' ;  'donkeys']            NULL
    ## 68                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 69                                              ['goats']            NULL
    ## 70             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 71                       ['oxen' ;  'goats' ;  'poultry']            NULL
    ## 72                                               ['pigs']            NULL
    ## 73  ['oxen' ;  'cows' ;  'goats' ;  'sheep' ;  'poultry']            NULL
    ## 74                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 75                                              ['goats']            NULL
    ## 76                                               ['none']            NULL
    ## 77                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 78                                     ['oxen' ;  'cows']            NULL
    ## 79                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 80                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 81                                     ['oxen' ;  'cows']            NULL
    ## 82                                     ['oxen' ;  'cows']            NULL
    ## 83             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 84                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 85                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 86                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 87                                               ['none']            NULL
    ## 88                                     ['oxen' ;  'cows']            NULL
    ## 89                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 90                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 91                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 92             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 93                                     ['oxen' ;  'cows']            NULL
    ## 94                                     ['oxen' ;  'cows']            NULL
    ## 95                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 96                                              ['goats']            NULL
    ## 97   ['oxen' ;  'cows' ;  'goats' ;  'pigs' ;  'poultry']            NULL
    ## 98                                    ['cows' ;  'goats']            NULL
    ## 99                                     ['oxen' ;  'cows']            NULL
    ## 100                                              ['none']            NULL
    ## 101               ['oxen' ;  'cows' ;  'goats' ;  'pigs']            NULL
    ## 102                                 ['cows' ;  'poultry']            NULL
    ## 103                                    ['oxen' ;  'cows']            NULL
    ## 104                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 105                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 106            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 107                                              ['none']            NULL
    ## 108                                    ['oxen' ;  'cows']            NULL
    ## 109            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 110                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 111            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 112                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 113                                              ['none']            NULL
    ## 114              ['oxen' ;  'cows' ;  'goats' ;  'sheep']            NULL
    ## 115                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 116                                              ['cows']            NULL
    ## 117                                              ['none']            NULL
    ## 118                                    ['oxen' ;  'cows']            NULL
    ## 119                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 120                                             ['goats']            NULL
    ## 121                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 122                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 123            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 124                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 125                                              ['cows']            NULL
    ## 126                                              ['none']            NULL
    ## 127                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 128                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 129                                           ['poultry']            NULL
    ## 130                                    ['oxen' ;  'cows']            NULL
    ## 131                         ['oxen' ;  'goats' ;  'pigs']            NULL
    ##     v_count poultry du_look_aftr_cows
    ## 1         1     yes                no
    ## 2         3     yes                no
    ## 3         1     yes                no
    ## 4         2     yes                no
    ## 5         4     yes                no
    ## 6         1      no                no
    ## 7         1      no                no
    ## 8         2     yes                no
    ## 9         3     yes                no
    ## 10        2     yes                no
    ## 11        2      no                no
    ## 12        2     yes                no
    ## 13        3     yes                no
    ## 14        3     yes                no
    ## 15        3     yes                no
    ## 16        4      no                no
    ## 17        1      no               yes
    ## 18        3     yes                no
    ## 19        2     yes                no
    ## 20        1     yes               yes
    ## 21        3     yes                no
    ## 22        1     yes                no
    ## 23        3     yes                no
    ## 24        3      no                no
    ## 25        2     yes                no
    ## 26        2     yes                no
    ## 27        3     yes                no
    ## 28        1     yes                no
    ## 29        1     yes                no
    ## 30        1      no                no
    ## 31        1      no                no
    ## 32        5     yes                no
    ## 33        2     yes                no
    ## 34        3     yes                no
    ## 35        2     yes                no
    ## 36        3      no                no
    ## 37        2     yes                no
    ## 38        3     yes               yes
    ## 39        1     yes                no
    ## 40        1     yes                no
    ## 41        2      no                no
    ## 42        3     yes                no
    ## 43        2      no                no
    ## 44        3     yes                no
    ## 45        4      no                no
    ## 46        2      no                no
    ## 47        1      no                no
    ## 48        3     yes                no
    ## 49        2     yes                no
    ## 50        1     yes                no
    ## 51        1      no                no
    ## 52        3     yes                no
    ## 53        2     yes                no
    ## 54        1     yes                no
    ## 55        1     yes                no
    ## 56        2     yes                no
    ## 57        1      no                no
    ## 58        3      no                no
    ## 59        3      no                no
    ## 60        4     yes                no
    ## 61        3     yes                no
    ## 62        1      no                no
    ## 63        1      no                no
    ## 64        1     yes                no
    ## 65        3     yes                no
    ## 66        4     yes                no
    ## 67        4     yes                no
    ## 68        3     yes                no
    ## 69        1     yes                no
    ## 70        4      no                no
    ## 71        3      no                no
    ## 72        1      no                no
    ## 73        5     yes                no
    ## 74        3     yes               yes
    ## 75        1     yes                no
    ## 76        1     yes                no
    ## 77        3      no                no
    ## 78        2     yes                no
    ## 79        3     yes                no
    ## 80        3     yes                no
    ## 81        2     yes                no
    ## 82        2      no                no
    ## 83        4     yes                no
    ## 84        3      no                no
    ## 85        3     yes                no
    ## 86        3     yes               yes
    ## 87        1     yes                no
    ## 88        2     yes                no
    ## 89        3     yes                no
    ## 90        3     yes                no
    ## 91        3     yes                no
    ## 92        4     yes                no
    ## 93        2      no                no
    ## 94        2     yes                no
    ## 95        3      no                no
    ## 96        1      no               yes
    ## 97        5     yes                no
    ## 98        2      no                no
    ## 99        2      no                no
    ## 100       1     yes                no
    ## 101       4     yes                no
    ## 102       2     yes               yes
    ## 103       2     yes                no
    ## 104       3     yes                no
    ## 105       3     yes                no
    ## 106       4      no                no
    ## 107       1     yes                no
    ## 108       2      no               yes
    ## 109       4      no                no
    ## 110       3     yes                no
    ## 111       4     yes                no
    ## 112       3     yes                no
    ## 113       1     yes                no
    ## 114       4     yes                no
    ## 115       3     yes                no
    ## 116       1      no               yes
    ## 117       1      no                no
    ## 118       2     yes                no
    ## 119       3     yes                no
    ## 120       1     yes                no
    ## 121       3     yes               yes
    ## 122       3     yes                no
    ## 123       4     yes               yes
    ## 124       3     yes                no
    ## 125       1     yes                no
    ## 126       1     yes                no
    ## 127       3     yes                no
    ## 128       3      no                no
    ## 129       1      no                no
    ## 130       2     yes                no
    ## 131       3     yes                no
    ##                                                                                                                                                                                                            items_owned
    ## 1                                                                                                                                                              ['bicycle' ;  'television' ;  'solar_panel' ;  'table']
    ## 2                                                                                                  ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 3                                                                                                                                                                                                      ['solar_torch']
    ## 4                                                                                                                                            ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 5                                                                                                                                                           ['motorcyle' ;  'radio' ;  'cow_plough' ;  'mobile_phone']
    ## 6                                                                                                                                                                                                                 NULL
    ## 7                                                                                                                                                                                        ['motorcyle' ;  'cow_plough']
    ## 8                                                                                       ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'fridge']
    ## 9                                                                                                                                                                     ['television' ;  'solar_panel' ;  'solar_torch']
    ## 10                                                                                    ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table']
    ## 11                                                                                                                                                                                           ['radio' ;  'cow_plough']
    ## 12                                                                                                                                                     ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 13                                                                                                                                                            ['bicycle' ;  'radio' ;  'cow_plough' ;  'mobile_phone']
    ## 14                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 15                                                                                                                                                  ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table']
    ## 16                                                                                                                                                         ['radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch']
    ## 17                                                                                                                                                                                                    ['mobile_phone']
    ## 18                                                                                                                                                                                       ['bicycle' ;  'mobile_phone']
    ## 19                                                                                                                          ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 20                                                                                                                                                                        ['bicycle' ;  'cow_plough' ;  'solar_torch']
    ## 21                                                                                                                                                                                                                NULL
    ## 22                                                                                                                                                                                                           ['radio']
    ## 23                                                                                            ['cow_cart' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'electricity' ;  'mobile_phone']
    ## 24                                                                                                                                                                ['radio' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 25                                                                 ['cow_cart' ;  'motorcyle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 26                                                                                                                                                              ['radio' ;  'cow_plough' ;  'table' ;  'mobile_phone']
    ## 27                                                                                                                          ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 28                                                                                                                                                                                                                NULL
    ## 29                                                                                                                                                  ['motorcyle' ;  'bicycle' ;  'radio' ;  'table' ;  'mobile_phone']
    ## 30                                                                                                                                                                            ['bicycle' ;  'radio' ;  'mobile_phone']
    ## 31                                                                                                                                                                                                                NULL
    ## 32                                                                                                                           ['cow_cart' ;  'motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 33                                                                                                               ['cow_cart' ;  'lorry' ;  'motorcyle' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 34                                                                                                            ['television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 35                                                                                                                                                                                         ['bicycle' ;  'cow_plough']
    ## 36                                                                                                                             ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 37                                                                                                          ['bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 38                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 39                                                                                                                                                                                                                NULL
    ## 40                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 41                                                                                                                                                    ['motorcyle' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 42                                                                                                                                                                                                    ['mobile_phone']
    ## 43                                                                                                                                                                                    ['cow_plough' ;  'mobile_phone']
    ## 44                                                                                                                                                                                          ['radio' ;  'solar_torch']
    ## 45                                                                                ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 46                                                                                              ['motorcyle' ;  'computer' ;  'television' ;  'sterio' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 47                                                                                                                                                                                   ['solar_torch' ;  'mobile_phone']
    ## 48                                                                                                                                                                                                           ['radio']
    ## 49                                                                                                               ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 50                                                                                                                                                                                                     ['solar_torch']
    ## 51                                                                                                                                                                                                           ['radio']
    ## 52                                                                                                                         ['motorcyle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 53                                                                                                                                                                            ['bicycle' ;  'radio' ;  'mobile_phone']
    ## 54                                                                                                                                                                                                                NULL
    ## 55                                                                                                                                                                    ['television' ;  'cow_plough' ;  'mobile_phone']
    ## 56                                                                                                                                                                        ['motorcyle' ;  'bicycle' ;  'mobile_phone']
    ## 57                                                                                                                                                                                                           ['radio']
    ## 58                                                                                                            ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 59                                                                                                                                                                                                                NULL
    ## 60                                                                                                                                                                                                      ['cow_plough']
    ## 61                                                                                   ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 62                                                                                                                                                                            ['bicycle' ;  'radio' ;  'mobile_phone']
    ## 63                                                                                                                                                                                                                NULL
    ## 64                                                                                                                                             ['bicycle' ;  'solar_torch' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 65                                                                                                                                                                 ['motorcyle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 66                                                                             ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 67                                                                                                                                         ['motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 68                                                                                                                                        ['motorcyle' ;  'television' ;  'sterio' ;  'solar_panel' ;  'mobile_phone']
    ## 69                                                                                                                                                           ['bicycle' ;  'radio' ;  'solar_torch' ;  'mobile_phone']
    ## 70                                                                                                                             ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 71                                                                                                                                                                         ['radio' ;  'cow_plough' ;  'mobile_phone']
    ## 72                                                                                                                                                                                                    ['mobile_phone']
    ## 73  ['cow_cart' ;  'car' ;  'lorry' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'electricity' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 74                                                                                                                ['motorcyle' ;  'bicycle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 75                                                                                                                                                                                                                NULL
    ## 76                                                                                                                                                                                                     ['electricity']
    ## 77                                                                                                                                                        ['radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 78                                                                                                                                    ['motorcyle' ;  'television' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 79                                                                                                                                                                                     ['cow_plough' ;  'solar_panel']
    ## 80                                                                                              ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 81                                                                                                                                                                                                     ['solar_panel']
    ## 82                                                                                                                                                                                    ['cow_plough' ;  'mobile_phone']
    ## 83                                                                             ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 84                                                                                                                                               ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_torch']
    ## 85                                                                                                                                                                         ['radio' ;  'cow_plough' ;  'mobile_phone']
    ## 86                                                                                                                ['bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 87                                                                                                                                                                                                                NULL
    ## 88                                                                                                                                                           ['bicycle' ;  'radio' ;  'solar_torch' ;  'mobile_phone']
    ## 89                                                                                                              ['cow_cart' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 90                                                                                                                                                                              ['bicycle' ;  'radio' ;  'cow_plough']
    ## 91                                                                                   ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 92                                                                                                                                           ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 93                                                                                                                                                                          ['radio' ;  'cow_plough' ;  'solar_torch']
    ## 94                                                                                                                                                                                           ['radio' ;  'cow_plough']
    ## 95                                                                                                               ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 96                                                                                                                                                                                        ['bicycle' ;  'solar_torch']
    ## 97                                                                                                                                       ['cow_cart' ;  'cow_plough' ;  'solar_panel' ;  'sofa_set' ;  'mobile_phone']
    ## 98                                                                                                                                                           ['cow_plough' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 99                                                                                                                                                                                                      ['cow_plough']
    ## 100                                                                                                                             ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch']
    ## 101                                                                                                                                                                          ['cow_cart' ;  'bicycle' ;  'cow_plough']
    ## 102                                                                                                                                        ['motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 103                                                                     ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 104                                                                                                                                                    ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 105                                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'table' ;  'mobile_phone']
    ## 106                                                                                 ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 107                                                                                                                                                                       ['radio' ;  'solar_torch' ;  'mobile_phone']
    ## 108                                                                                                                         ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 109                                                                                                                                                     ['bicycle' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 110                                                                 ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 111                                                                                                                 ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 112                                                                               ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 113                                                                                                            ['motorcyle' ;  'television' ;  'radio' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 114                                                                                             ['cow_cart' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 115                                                                                               ['cow_cart' ;  'motorcyle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 116                                                                                                                                                                                                   ['mobile_phone']
    ## 117                                                                                                                                                                        ['radio' ;  'solar_panel' ;  'solar_torch']
    ## 118                                                                                                                                                    ['cow_cart' ;  'cow_plough' ;  'solar_torch' ;  'mobile_phone']
    ## 119                                       ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_torch' ;  'electricity' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 120                                                                                                                                                                     ['bicycle' ;  'solar_torch' ;  'mobile_phone']
    ## 121                                                                                                            ['motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 122                                                  ['car' ;  'lorry' ;  'motorcyle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 123                                                                                                    ['motorcyle' ;  'bicycle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 124                                                                                                                 ['motorcyle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 125                                                                                                                                      ['radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 126                                                                                                  ['bicycle' ;  'television' ;  'radio' ;  'sterio' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 127                                                                                                                                                                          ['motorcyle' ;  'radio' ;  'solar_panel']
    ## 128                                                 ['car' ;  'lorry' ;  'television' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_torch' ;  'electricity' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 129                                                                                                                                                      ['radio' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 130                                   ['cow_cart' ;  'lorry' ;  'motorcyle' ;  'computer' ;  'television' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'electricity' ;  'mobile_phone']
    ## 131                                                                                                                           ['radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ##     items_owned_other no_meals
    ## 1                NULL        2
    ## 2                NULL        2
    ## 3                NULL        2
    ## 4                NULL        2
    ## 5                NULL        2
    ## 6                NULL        2
    ## 7                NULL        3
    ## 8                NULL        2
    ## 9                NULL        3
    ## 10               NULL        3
    ## 11               NULL        2
    ## 12               NULL        3
    ## 13               NULL        2
    ## 14               NULL        3
    ## 15               NULL        2
    ## 16               NULL        3
    ## 17               NULL        2
    ## 18               NULL        2
    ## 19               NULL        3
    ## 20               NULL        2
    ## 21               NULL        2
    ## 22               NULL        2
    ## 23               NULL        3
    ## 24               NULL        2
    ## 25               NULL        2
    ## 26               NULL        2
    ## 27               NULL        3
    ## 28               NULL        3
    ## 29               NULL        3
    ## 30               NULL        2
    ## 31               NULL        3
    ## 32               NULL        2
    ## 33               NULL        2
    ## 34               NULL        2
    ## 35               NULL        3
    ## 36               NULL        3
    ## 37               NULL        3
    ## 38               NULL        3
    ## 39               NULL        3
    ## 40               NULL        3
    ## 41               NULL        3
    ## 42               NULL        3
    ## 43               NULL        2
    ## 44               NULL        2
    ## 45               NULL        3
    ## 46               NULL        2
    ## 47               NULL        3
    ## 48               NULL        3
    ## 49               NULL        3
    ## 50               NULL        2
    ## 51               NULL        3
    ## 52               NULL        3
    ## 53               NULL        2
    ## 54               NULL        2
    ## 55               NULL        2
    ## 56               NULL        3
    ## 57               NULL        2
    ## 58               NULL        2
    ## 59               NULL        2
    ## 60               NULL        2
    ## 61               NULL        3
    ## 62               NULL        3
    ## 63               NULL        3
    ## 64               NULL        3
    ## 65               NULL        3
    ## 66               NULL        3
    ## 67               NULL        3
    ## 68               NULL        3
    ## 69               NULL        3
    ## 70               NULL        2
    ## 71               NULL        2
    ## 72               NULL        2
    ## 73               NULL        3
    ## 74               NULL        3
    ## 75               NULL        2
    ## 76               NULL        2
    ## 77               NULL        3
    ## 78               NULL        3
    ## 79               NULL        3
    ## 80               NULL        3
    ## 81               NULL        3
    ## 82               NULL        3
    ## 83               NULL        3
    ## 84               NULL        2
    ## 85               NULL        3
    ## 86               NULL        2
    ## 87               NULL        3
    ## 88               NULL        2
    ## 89               NULL        3
    ## 90               NULL        2
    ## 91               NULL        3
    ## 92               NULL        3
    ## 93               NULL        2
    ## 94               NULL        2
    ## 95               NULL        3
    ## 96               NULL        3
    ## 97               NULL        3
    ## 98               NULL        3
    ## 99               NULL        2
    ## 100              NULL        3
    ## 101              NULL        3
    ## 102              NULL        3
    ## 103              NULL        3
    ## 104              NULL        3
    ## 105              NULL        2
    ## 106              NULL        3
    ## 107              NULL        3
    ## 108              NULL        3
    ## 109              NULL        3
    ## 110              NULL        3
    ## 111              NULL        3
    ## 112              NULL        3
    ## 113              NULL        3
    ## 114              NULL        2
    ## 115              NULL        3
    ## 116              NULL        3
    ## 117              NULL        3
    ## 118              NULL        2
    ## 119              NULL        3
    ## 120              NULL        2
    ## 121              NULL        2
    ## 122              NULL        3
    ## 123              NULL        2
    ## 124              NULL        3
    ## 125              NULL        2
    ## 126              NULL        3
    ## 127              NULL        3
    ## 128              NULL        3
    ## 129              NULL        3
    ## 130              NULL        3
    ## 131              NULL        3
    ##                                                                                         months_lack_food
    ## 1                                                                                                ['Jan']
    ## 2                                                           ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 3                                                   ['Jan' ;  'Feb' ;  'Mar' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 4                                                                    ['Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 5                                                                    ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 6                                                                             ['Aug' ;  'Sept' ;  'Oct']
    ## 7                                                                                                ['Nov']
    ## 8                                                                                                ['Jan']
    ## 9                                                                                       ['Jan' ;  'Dec']
    ## 10                                                                    ['Jan' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 11                                                                                      ['Oct' ;  'Nov']
    ## 12                                                                                     ['Sept' ;  'Oct']
    ## 13                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 14                                               ['June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 15  ['Jan' ;  'Feb' ;  'Mar' ;  'Apr' ;  'May' ;  'June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 16                                                                                      ['Jan' ;  'Feb']
    ## 17                                                                                      ['Nov' ;  'Dec']
    ## 18                                                                                      ['Oct' ;  'Nov']
    ## 19                                                                             ['Oct' ;  'Nov' ;  'Dec']
    ## 20                                                                                      ['Oct' ;  'Nov']
    ## 21                                                  ['Jan' ;  'Feb' ;  'Mar' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 22                      ['Jan' ;  'Feb' ;  'Mar' ;  'Apr' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 23                                                                                              ['none']
    ## 24                                                                                      ['Nov' ;  'Dec']
    ## 25                                                                             ['Jan' ;  'Feb' ;  'Oct']
    ## 26                                                                                              ['none']
    ## 27                                                                                              ['none']
    ## 28                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 29                                                                                      ['Jan' ;  'Feb']
    ## 30                                                                                      ['Jan' ;  'Feb']
    ## 31                                                                                              ['none']
    ## 32                                                                                              ['none']
    ## 33                                                                                              ['none']
    ## 34                                                                                      ['Jan' ;  'Dec']
    ## 35                                                          ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 36                                                                                              ['none']
    ## 37                                                                             ['Jan' ;  'Nov' ;  'Dec']
    ## 38                                                                                               ['Nov']
    ## 39                                                                                               ['Nov']
    ## 40                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 41                                                                                      ['Oct' ;  'Nov']
    ## 42                                                                             ['Jan' ;  'Nov' ;  'Dec']
    ## 43                                                           ['Jan' ;  'Feb' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 44                                                                                      ['Jan' ;  'Dec']
    ## 45                                                                                              ['none']
    ## 46                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 47                                                                                              ['none']
    ## 48                                               ['June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 49                                                                             ['Jan' ;  'Nov' ;  'Dec']
    ## 50                                      ['June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 51                                                                                      ['Oct' ;  'Nov']
    ## 52                                                                   ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 53                                                                                               ['Nov']
    ## 54                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 55                                                                                      ['Oct' ;  'Nov']
    ## 56                                                                                              ['none']
    ## 57                                                                                              ['none']
    ## 58                                                                                              ['none']
    ## 59                                                                                              ['none']
    ## 60                                                                                              ['none']
    ## 61                                                                             ['Jan' ;  'Feb' ;  'Dec']
    ## 62                                                                   ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 63                                                                    ['Jan' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 64                                                                             ['Jan' ;  'Feb' ;  'Dec']
    ## 65                                                                             ['Jan' ;  'Feb' ;  'Mar']
    ## 66                                                                                              ['none']
    ## 67                                                                                              ['none']
    ## 68                                                                                              ['none']
    ## 69                                                                                              ['none']
    ## 70                                                                                              ['none']
    ## 71                                                                   ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 72                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 73                                                                             ['Jan' ;  'Oct' ;  'Nov']
    ## 74                                                                                              ['none']
    ## 75                                                                                      ['Oct' ;  'Nov']
    ## 76                                                          ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 77                                                                                              ['none']
    ## 78                                                                                               ['Nov']
    ## 79                                                                                      ['Oct' ;  'Nov']
    ## 80                                                                                              ['none']
    ## 81                                                                    ['Jan' ;  'Feb' ;  'Nov' ;  'Dec']
    ## 82                                                                                              ['none']
    ## 83                                                                                              ['none']
    ## 84                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 85                                                                                              ['none']
    ## 86                                                                                               ['Nov']
    ## 87                                                                                               ['Nov']
    ## 88                                                                             ['Oct' ;  'Nov' ;  'Dec']
    ## 89                                                  ['Jan' ;  'Feb' ;  'Mar' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 90                                                 ['Jan' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 91                                                                            ['Jan' ;  'Sept' ;  'Oct']
    ## 92                                                                                              ['none']
    ## 93                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 94                                                                                      ['Oct' ;  'Nov']
    ## 95                                                                                      ['Oct' ;  'Nov']
    ## 96                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 97                                                                             ['Jan' ;  'Feb' ;  'Dec']
    ## 98                                                                                      ['Jan' ;  'Feb']
    ## 99                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 100                                                                                             ['none']
    ## 101                                                                            ['Jan' ;  'Feb' ;  'Dec']
    ## 102                                                                            ['Jan' ;  'Feb' ;  'Dec']
    ## 103                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 104                                                        ['July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 105                                                                                             ['none']
    ## 106                                                                                             ['none']
    ## 107                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 108                                                         ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 109                                                                                             ['none']
    ## 110                                                                                             ['none']
    ## 111                                                                  ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 112                                                                            ['Jan' ;  'Nov' ;  'Dec']
    ## 113                                                                   ['Jan' ;  'Feb' ;  'Nov' ;  'Dec']
    ## 114                                                                                             ['none']
    ## 115                                                                                     ['Jan' ;  'Dec']
    ## 116                                                                           ['Sept' ;  'Oct' ;  'Nov']
    ## 117                                                                           ['Sept' ;  'Oct' ;  'Nov']
    ## 118                                                                                              ['Nov']
    ## 119                                                                                             ['none']
    ## 120                                                                                     ['Feb' ;  'Mar']
    ## 121                                                                            ['Jan' ;  'Nov' ;  'Dec']
    ## 122                                                                            ['Jan' ;  'Feb' ;  'Dec']
    ## 123                                                                   ['Jan' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 124                                                                                              ['Nov']
    ## 125                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 126                                                                            ['Jan' ;  'Nov' ;  'Dec']
    ## 127                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 128                                                                                             ['none']
    ## 129                                                                           ['Sept' ;  'Oct' ;  'Nov']
    ## 130                                                                                     ['Nov' ;  'Dec']
    ## 131                                                                                     ['Oct' ;  'Nov']
    ##                                                                                                                                   no_food_mitigation
    ## 1                                                                                 ['na' ;  'rely_less_food' ;  'reduce_meals' ;  'day_night_hungry']
    ## 2                                                                ['na' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'seek_government']
    ## 3                                                                                                       ['na' ;  'restrict_adults' ;  'lab_ex_food']
    ## 4                                                                                     ['na' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 5                                                                                                                 ['na' ;  'go_forest' ;  'migrate']
    ## 6                                                                                              ['borrow_food' ;  'lab_ex_food' ;  'seek_government']
    ## 7                                                                                                                                    ['lab_ex_food']
    ## 8                                                      ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food']
    ## 9                                                     ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 10                                                                       ['rely_less_food' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 11                                                                                                               ['rely_less_food' ;  'lab_ex_food']
    ## 12                                                                          ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'lab_ex_food']
    ## 13                                                                                                                                   ['lab_ex_food']
    ## 14                                                                                                                 ['reduce_meals' ;  'lab_ex_food']
    ## 15                                                                  ['na' ;  'rely_less_food' ;  'limit_portion' ;  'reduce_meals' ;  'lab_ex_food']
    ## 16                                                                                                                                   ['lab_ex_food']
    ## 17                                                                                                                                   ['lab_ex_food']
    ## 18                                                                                                                 ['reduce_meals' ;  'lab_ex_food']
    ## 19                                                                       ['rely_less_food' ;  'limit_portion' ;  'lab_ex_food' ;  'seek_government']
    ## 20                                                                                                               ['rely_less_food' ;  'lab_ex_food']
    ## 21                                                                    ['rely_less_food' ;  'restrict_adults' ;  'day_night_hungry' ;  'lab_ex_food']
    ## 22                                                                              ['rely_less_food' ;  'reduce_meals' ;  'go_forest' ;  'lab_ex_food']
    ## 23                                                                                                                                            ['na']
    ## 24                                                                                                                                   ['lab_ex_food']
    ## 25                                                                                                                                            ['na']
    ## 26                                                                                                                                            ['na']
    ## 27                                                                                                                                            ['na']
    ## 28                                                             ['rely_less_food' ;  'reduce_meals' ;  'borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 29                                                                                                             ['rely_less_food' ;  'limit_variety']
    ## 30                                                    ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 31                                                                                                                                            ['na']
    ## 32                                                                                                                                            ['na']
    ## 33                                                                                                                                            ['na']
    ## 34                                                    ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 35                                    ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'restrict_adults' ;  'go_forest']
    ## 36                                                                                                                                            ['na']
    ## 37                                                                                            ['rely_less_food' ;  'limit_variety' ;  'lab_ex_food']
    ## 38                                                                                                                ['limit_variety' ;  'lab_ex_food']
    ## 39                                                                                                                                   ['lab_ex_food']
    ## 40                                                                                                                                   ['lab_ex_food']
    ## 41                                                                                                               ['limit_portion' ;  'reduce_meals']
    ## 42                                                                                           ['rely_less_food' ;  'limit_variety' ;  'reduce_meals']
    ## 43                                                                                                                                   ['lab_ex_food']
    ## 44                                                                                                                                   ['borrow_food']
    ## 45                                                                                                                                            ['na']
    ## 46                                                                                                                                   ['lab_ex_food']
    ## 47                                                                                                                                            ['na']
    ## 48                                                                                                                                 ['limit_variety']
    ## 49                                                                                                  ['reduce_meals' ;  'go_forest' ;  'lab_ex_food']
    ## 50                                                                                                   ['borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 51                                                                                                                    ['go_forest' ;  'lab_ex_food']
    ## 52                                                                                                               ['limit_variety' ;  'reduce_meals']
    ## 53                                                                                                             ['rely_less_food' ;  'limit_portion']
    ## 54                                                                                                               ['rely_less_food' ;  'lab_ex_food']
    ## 55                                                                                                                                   ['lab_ex_food']
    ## 56                                                                                                                                            ['na']
    ## 57                                                                                                                                            ['na']
    ## 58                                                                                                                                            ['na']
    ## 59                                                                                                                                            ['na']
    ## 60                                                                                                                                            ['na']
    ## 61                                                                      ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults']
    ## 62  ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 63                                                                      ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults']
    ## 64                                                     ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 65                                                                          ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'lab_ex_food']
    ## 66                                                                                                                                            ['na']
    ## 67                                                                                                                                            ['na']
    ## 68                                                                                                                                            ['na']
    ## 69                                                                                                                                            ['na']
    ## 70                                                                                                                                            ['na']
    ## 71                 ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'lab_ex_food']
    ## 72                                                                                                                  ['borrow_food' ;  'lab_ex_food']
    ## 73                                                                                                                                            ['na']
    ## 74                                                                                                                                            ['na']
    ## 75                                     ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'no_food' ;  'day_night_hungry']
    ## 76                                                              ['limit_variety' ;  'reduce_meals' ;  'borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 77                                                                                                                                            ['na']
    ## 78                                                                                                                                            ['na']
    ## 79                                                                                             ['rely_less_food' ;  'reduce_meals' ;  'lab_ex_food']
    ## 80                                                                                                                                            ['na']
    ## 81                                                                                                                                            ['na']
    ## 82                                                                                                                                            ['na']
    ## 83                                                                                                                                            ['na']
    ## 84                                                                                                                                   ['lab_ex_food']
    ## 85                                                                                                                                            ['na']
    ## 86                                                                                           ['rely_less_food' ;  'limit_variety' ;  'reduce_meals']
    ## 87                                                                                                                 ['reduce_meals' ;  'lab_ex_food']
    ## 88                                                                                                                  ['borrow_food' ;  'lab_ex_food']
    ## 89                                                     ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 90                                                       ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'lab_ex_food']
    ## 91                                                                                                             ['rely_less_food' ;  'limit_variety']
    ## 92                                                                                                                                            ['na']
    ## 93                                                                                                                  ['borrow_food' ;  'lab_ex_food']
    ## 94                                                                                                                                            ['na']
    ## 95                                                                             ['rely_less_food' ;  'limit_variety' ;  'go_forest' ;  'lab_ex_food']
    ## 96                                    ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'lab_ex_food']
    ## 97                                                                                                                                     ['go_forest']
    ## 98                                                                                                                                   ['lab_ex_food']
    ## 99                                                                                                                                            ['na']
    ## 100                                                                                                                                           ['na']
    ## 101                                                                                                                   ['go_forest' ;  'lab_ex_food']
    ## 102                                                                                                                                  ['lab_ex_food']
    ## 103                                                                                                             ['lab_ex_food' ;  'seek_government']
    ## 104                                                                                          ['rely_less_food' ;  'limit_portion' ;  'reduce_meals']
    ## 105                                                                                                                                           ['na']
    ## 106                                                                                                                                           ['na']
    ## 107                                                        ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'borrow_food' ;  'lab_ex_food']
    ## 108                                                                                                                 ['borrow_food' ;  'lab_ex_food']
    ## 109                                                                                                                                           ['na']
    ## 110                                                                                                                                           ['na']
    ## 111                                                                                          ['rely_less_food' ;  'limit_portion' ;  'reduce_meals']
    ## 112                                                                         ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'lab_ex_food']
    ## 113                                   ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'lab_ex_food']
    ## 114                                                                                                                                           ['na']
    ## 115                                                                                                            ['rely_less_food' ;  'limit_variety']
    ## 116                                                                                                                ['reduce_meals' ;  'lab_ex_food']
    ## 117                                                                                                                                  ['lab_ex_food']
    ## 118                                                                                                                                  ['lab_ex_food']
    ## 119                                                                                                                                           ['na']
    ## 120                                                                                                                   ['go_forest' ;  'lab_ex_food']
    ## 121                                                                                                                                  ['lab_ex_food']
    ## 122                                                                                                                                  ['lab_ex_food']
    ## 123                                                                                                                                           ['na']
    ## 124                                                                                                                                           ['na']
    ## 125                                                                                                                   ['go_forest' ;  'lab_ex_food']
    ## 126                                                                                                                                  ['borrow_food']
    ## 127                                                                                                              ['rely_less_food' ;  'lab_ex_food']
    ## 128                                                                                                                                           ['na']
    ## 129                                                                                                                                  ['lab_ex_food']
    ## 130                                                    ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 131                                                                                         ['rely_less_food' ;  'restrict_adults' ;  'borrow_food']
    ##      Latitude Longitude Altitude Accuracy
    ## 1   -19.11226  33.48346      698   14.000
    ## 2   -19.11248  33.48342      690   19.000
    ## 3   -19.11211  33.48345      674   13.000
    ## 4   -19.11223  33.48342      679    5.000
    ## 5   -19.11222  33.48343      689   10.000
    ## 6   -19.11220  33.48339      692   12.000
    ## 7   -19.11222  33.48336      709   11.000
    ## 8   -19.11216  33.48342      700    9.000
    ## 9   -19.11222  33.48344      701   11.000
    ## 10  -19.11221  33.48339      710   14.000
    ## 11  -19.11219  33.48346      707   10.000
    ## 12  -19.11229  33.48342      696   13.000
    ## 13  -19.11237  33.48356      706   15.000
    ## 14  -19.11222  33.48344      698   11.000
    ## 15  -19.11208  33.48340      715    9.000
    ## 16  -19.11211  33.48344      709    9.000
    ## 17  -19.11218  33.48346      710   10.000
    ## 18  -19.11134  33.47631      685   17.000
    ## 19  -19.11143  33.47641      716   30.000
    ## 20  -19.11147  33.47619      700   27.000
    ## 21  -19.11155  33.47623      707   20.000
    ## 22  -19.11213  33.48351      722    9.000
    ## 23  -19.11219  33.48338      699   10.000
    ## 24  -19.11219  33.48343      745   11.000
    ## 25  -19.11223  33.48348      698   11.000
    ## 26  -19.11230  33.48354      706   12.000
    ## 27  -19.04300  33.40508      679   14.000
    ## 28  -19.04291  33.40507      721    7.000
    ## 29  -19.04302  33.40507      657    6.000
    ## 30  -19.04300  33.40505      669    5.000
    ## 31  -19.04302  33.40509      704    4.000
    ## 32  -19.04411  33.40391      703    8.000
    ## 33  -19.04415  33.40384      695    5.000
    ## 34  -19.11219  33.48342      706   11.000
    ## 35  -19.11211  33.48343      733   11.000
    ## 36  -19.11218  33.48338      710   10.000
    ## 37  -19.11218  33.48340      711   12.000
    ## 38  -19.11223  33.48337      696    9.000
    ## 39  -19.04336  33.40467        0   20.000
    ## 40  -19.04336  33.40467        0   22.112
    ## 41  -19.04339  33.40485      679   13.000
    ## 42  -19.04346  33.40485      699   10.000
    ## 43  -19.04303  33.40473      605   30.000
    ## 44  -19.04315  33.40458      716   11.000
    ## 45  -19.04312  33.40466      703   28.000
    ## 46  -19.04307  33.40458      703    5.000
    ## 47  -19.11226  33.48340      689    5.000
    ## 48  -19.11223  33.48353      689   12.000
    ## 49  -19.11228  33.48335      694   12.000
    ## 50  -19.11220  33.48345      718   12.000
    ## 51  -19.11221  33.48338      709   12.000
    ## 52  -19.11224  33.48335      694   10.000
    ## 53  -19.11217  33.48344      687   10.000
    ## 54  -19.11220  33.48336      681    9.000
    ## 55  -19.11229  33.48333      702   11.000
    ## 56  -19.11217  33.48342      689   10.000
    ## 57  -19.11228  33.48339      695   10.000
    ## 58  -19.11218  33.48332      723   11.000
    ## 59  -19.11234  33.48333      683   13.000
    ## 60  -19.11226  33.48341      694   11.000
    ## 61  -19.11218  33.48342      712   13.000
    ## 62  -19.11217  33.48340      719   18.000
    ## 63  -19.11220  33.48339      702   25.000
    ## 64  -19.11220  33.48340      704    9.000
    ## 65  -19.11221  33.48341      706   39.000
    ## 66  -19.11217  33.48339      702    8.000
    ## 67  -19.11209  33.48339      717   11.000
    ## 68  -19.11215  33.48348      710   10.000
    ## 69  -19.11217  33.48340      708    8.000
    ## 70  -19.11217  33.48341      707    8.000
    ## 71  -19.11221  33.48333      696    4.000
    ## 72  -19.11221  33.48341      676    8.000
    ## 73  -19.10413  33.47776        0 2099.999
    ## 74  -19.11210  33.48345      702   11.000
    ## 75  -19.11224  33.48345      691   12.000
    ## 76  -19.11221  33.48342      713   13.000
    ## 77  -19.11236  33.48356      714   50.000
    ## 78  -19.11205  33.48349      713    9.000
    ## 79  -19.11205  33.48347      701    4.000
    ## 80  -19.11208  33.48351      701    5.000
    ## 81  -19.11204  33.48345      694    4.000
    ## 82  -19.11232  33.48346      690   10.000
    ## 83  -19.11223  33.48349      691   13.000
    ## 84  -19.11221  33.48342      706    9.000
    ## 85  -19.11220  33.48340      694   10.000
    ## 86  -19.11219  33.48338      714   11.000
    ## 87  -19.11212  33.48339      716    7.000
    ## 88  -19.11217  33.48339      685   10.000
    ## 89  -19.11219  33.48340      705    5.000
    ## 90  -19.11221  33.48347      716    5.000
    ## 91  -19.11220  33.48341      714    4.000
    ## 92  -19.11220  33.48342      702    9.000
    ## 93  -19.11232  33.48350      693   33.000
    ## 94  -19.11235  33.48359      697   10.000
    ## 95  -19.11232  33.48348      710   13.000
    ## 96  -19.11224  33.48342      702   11.000
    ## 97  -19.11219  33.48337      712    9.000
    ## 98  -19.04413  33.40389      691   11.000
    ## 99  -19.04403  33.40398      723   11.000
    ## 100 -19.04415  33.40390      689    6.000
    ## 101 -19.11226  33.48337      711    9.000
    ## 102 -19.11221  33.48351      735   11.000
    ## 103 -19.11221  33.48341      709    5.000
    ## 104 -19.11222  33.48338      699   10.000
    ## 105 -19.11220  33.48340      704    9.000
    ## 106 -19.11223  33.48341      706   12.000
    ## 107 -19.11221  33.48344      713    9.000
    ## 108 -19.11218  33.48341      682   11.000
    ## 109 -19.11226  33.48335      706    5.000
    ## 110 -19.11147  33.47610        0   20.000
    ## 111 -19.11147  33.47610        0   20.000
    ## 112 -19.11147  33.47610        0   20.000
    ## 113 -19.11147  33.47610        0   20.000
    ## 114 -19.11219  33.48342      710    5.000
    ## 115 -19.11248  33.47633        0 1911.000
    ## 116 -19.11148  33.47618      709   17.000
    ## 117 -19.11149  33.47618      712   28.000
    ## 118 -19.11218  33.48345      711   12.000
    ## 119 -19.11217  33.48347      708    9.000
    ## 120 -19.11386  33.48267        0 1799.999
    ## 121 -19.11499  33.48827        0 2000.000
    ## 122 -19.11217  33.48341      703    3.000
    ## 123 -19.11218  33.48336      705    5.000
    ## 124 -19.11217  33.48342      714    4.000
    ## 125 -19.11219  33.48338      709    9.000
    ## 126 -19.11215  33.48336      705    4.000
    ## 127 -19.11219  33.48338      700    7.000
    ## 128 -19.11216  33.48339      720    9.000
    ## 129 -19.11227  33.48347      719   10.000
    ## 130 -19.11228  33.48339      711    5.000
    ## 131 -19.11218  33.48337      681   20.000
    ##                                        anceID         start_clean
    ## 1   uuid:ec241f2c-0609-46ed-b5e8-fe575f6cefef 2017-03-23 09:49:57
    ## 2   uuid:099de9c9-3e5e-427b-8452-26250e840d6e 2017-04-02 09:48:16
    ## 3   uuid:193d7daf-9582-409b-bf09-027dd36f9007 2017-04-02 14:35:26
    ## 4   uuid:148d1105-778a-4755-aa71-281eadd4a973 2017-04-02 14:55:18
    ## 5   uuid:2c867811-9696-4966-9866-f35c3e97d02d 2017-04-02 15:10:35
    ## 6   uuid:daa56c91-c8e3-44c3-a663-af6a49a2ca70 2017-04-02 15:27:25
    ## 7   uuid:ae20a58d-56f4-43d7-bafa-e7963d850844 2017-04-02 15:38:01
    ## 8   uuid:d6cee930-7be1-4fd9-88c0-82a08f90fb5a 2017-04-02 15:59:52
    ## 9   uuid:846103d2-b1db-4055-b502-9cd510bb7b37 2017-04-02 16:23:36
    ## 10  uuid:8f4e49bc-da81-4356-ae34-e0d794a23721 2017-04-02 17:03:28
    ## 11  uuid:d29b44e3-3348-4afc-aa4d-9eb34c89d483 2017-04-03 03:16:15
    ## 12  uuid:e6ee6269-b467-4e37-91fc-5e9eaf934557 2017-04-03 03:31:13
    ## 13  uuid:6c00c145-ee3b-409c-8c02-2c8d743b6918 2017-04-03 03:58:43
    ## 14  uuid:9b21467f-1116-4340-a3b1-1ab64f13c87d 2017-04-03 04:19:57
    ## 15  uuid:a837e545-ff86-4a1c-a1a5-6186804b985f 2017-04-03 05:12:17
    ## 16  uuid:d17db52f-4b87-4768-b534-ea8f9704c565 2017-04-03 05:29:24
    ## 17  uuid:4707f3dc-df18-4348-9c2c-eec651e89b6b 2017-04-03 05:41:42
    ## 18  uuid:7ffe7bd1-a15c-420c-a137-e1f006c317a3 2017-04-03 12:27:04
    ## 19  uuid:e32f2dc0-0d05-42fb-8e21-605757ddf07d 2017-04-03 12:40:14
    ## 20  uuid:d1005274-bf52-4e79-8380-3350dd7c2bac 2017-04-03 14:04:50
    ## 21  uuid:6570a7d0-6a0b-452c-aa2e-922500e35749 2017-04-03 14:24:58
    ## 22  uuid:a51c3006-8847-46ff-9d4e-d29919b8ecf9 2017-04-03 16:28:52
    ## 23  uuid:58b37b6d-d6cd-4414-8790-b9c68bca98de 2017-04-03 16:41:04
    ## 24  uuid:661457d3-7e61-45e8-a238-7415e7548f82 2017-04-03 17:19:49
    ## 25  uuid:45ed84c4-114e-4df0-9f5d-c800806c2bee 2017-04-04 04:01:58
    ## 26  uuid:1c54ee24-22c4-4ee9-b1ad-42d483c08e2e 2017-04-04 04:30:19
    ## 27  uuid:3197cded-1fdc-4c0c-9b10-cfcc0bf49c4d 2017-04-05 04:59:42
    ## 28  uuid:1de53318-a8cf-4736-99b1-8239f8822473 2017-04-05 05:14:49
    ## 29  uuid:adcd7463-8943-4c67-b25f-f72311409476 2017-04-05 05:37:30
    ## 30  uuid:59341ead-92be-45a9-8545-6edf9f94fdc6 2017-04-05 06:05:58
    ## 31  uuid:cb06eb49-dd39-4150-8bbe-a599e074afe8 2017-04-05 06:21:20
    ## 32  uuid:25597af3-cd79-449c-a48a-fb9aea6c48bf 2017-04-05 06:38:55
    ## 33  uuid:0fbd2df1-2640-4550-9fbd-7317feaa4758 2017-04-05 08:08:19
    ## 34  uuid:14c78c45-a7cc-4b2a-b765-17c82b43feb4 2017-04-05 16:00:47
    ## 35  uuid:ff7496e7-984a-47d3-a8a1-13618b5683ce 2017-04-05 16:22:13
    ## 36  uuid:c90eade0-1148-4a12-8c0e-6387a36f45b1 2017-04-05 16:50:48
    ## 37  uuid:408c6c93-d723-45ef-8dee-1b1bd3fe20cd 2017-04-05 17:17:48
    ## 38  uuid:81309594-ff58-4dc1-83a7-72af5952ee08 2017-04-05 17:28:12
    ## 39  uuid:c0fb6310-55af-4831-ae3d-2729556c3285 2017-04-06 08:31:17
    ## 40  uuid:c0b34854-eede-4e81-b183-ef58a45bfc34 2017-04-06 08:44:51
    ## 41  uuid:b3ba34d8-eea1-453d-bc73-c141bcbbc5e5 2017-04-06 09:03:50
    ## 42  uuid:e3a1dd8a-1bda-428c-a014-2b527f11ae64 2017-04-06 09:14:22
    ## 43  uuid:b4dff49f-ef27-40e5-a9d1-acf287b47358 2017-04-06 09:31:56
    ## 44  uuid:f9fadf44-d040-4fca-86c1-2835f79c4952 2017-04-06 14:44:32
    ## 45  uuid:e3554d22-35b1-4fb9-b386-dd5866ad5792 2017-04-06 14:53:04
    ## 46  uuid:35f297e0-aa5d-4149-9b7b-4965004cfc37 2017-04-06 15:19:41
    ## 47  uuid:2d0b1936-4f82-4ec3-a3b5-7c3c8cd6cc2b 2017-04-07 14:05:25
    ## 48  uuid:e180899c-7614-49eb-a97c-40ed013a38a2 2017-04-07 14:19:49
    ## 49  uuid:2303ebc1-2b3c-475a-8916-b322ebf18440 2017-04-07 14:43:09
    ## 50  uuid:4267c33c-53a7-46d9-8bd6-b96f58a4f92c 2017-04-07 14:56:01
    ## 51  uuid:18ac8e77-bdaf-47ab-85a2-e4c947c9d3ce 2017-04-07 15:27:45
    ## 52  uuid:6db55cb4-a853-4000-9555-757b7fae2bcf 2017-04-08 04:44:09
    ## 53  uuid:cc7f75c5-d13e-43f3-97e5-4f4c03cb4b12 2017-04-08 05:03:08
    ## 54  uuid:273ab27f-9be3-4f3b-83c9-d3e1592de919 2017-04-08 05:36:55
    ## 55  uuid:883c0433-9891-4121-bc63-744f082c1fa0 2017-04-08 05:52:32
    ## 56  uuid:973c4ac6-f887-48e7-aeaf-4476f2cfab76 2017-04-08 06:05:59
    ## 57  uuid:a7184e55-0615-492d-9835-8f44f3b03a71 2017-04-08 06:26:22
    ## 58  uuid:a7a3451f-cd0d-4027-82d9-8dcd1234fcca 2017-04-08 08:25:49
    ## 59  uuid:1936db62-5732-45dc-98ff-9b3ac7a22518 2017-04-08 08:52:05
    ## 60  uuid:85465caf-23e4-4283-bb72-a0ef30e30176 2017-04-08 09:03:01
    ## 61  uuid:2401cf50-8859-44d9-bd14-1bf9128766f2 2017-04-08 10:47:11
    ## 62  uuid:c6597ecc-cc2a-4c35-a6dc-e62c71b345d6 2017-04-08 13:27:58
    ## 63  uuid:86ed4328-7688-462f-aac7-d6518414526a 2017-04-08 13:41:39
    ## 64  uuid:28cfd718-bf62-4d90-8100-55fafbe45d06 2017-04-08 13:52:30
    ## 65  uuid:143f7478-0126-4fbc-86e0-5d324339206b 2017-04-08 14:02:49
    ## 66  uuid:a457eab8-971b-4417-a971-2e55b8702816 2017-04-08 21:09:38
    ## 67  uuid:6c15d667-2860-47e3-a5e7-7f679271e419 2017-04-08 21:34:23
    ## 68  uuid:ef04b3eb-b47d-412e-9b09-4f5e08fc66f9 2017-04-08 21:49:40
    ## 69  uuid:f86933a5-12b8-4427-b821-43c5b039401d 2017-04-09 22:08:07
    ## 70  uuid:1feb0108-4599-4bf9-8a07-1f5e66a50a0a 2017-04-09 22:21:23
    ## 71  uuid:761f9c49-ec93-4932-ba4c-cc7b78dfcef1 2017-04-09 15:00:19
    ## 72  uuid:f6d04b41-b539-4e00-868a-0f62b427587d 2017-04-09 05:16:06
    ## 73  uuid:429d279a-a519-4dcc-9f64-4673b0fd5d53 2017-04-09 05:27:46
    ## 74  uuid:59738c17-1cda-49ee-a563-acd76f6bc487 2017-04-09 05:47:31
    ## 75  uuid:7e7961ca-fa1c-4567-9bfa-a02f876e4e03 2017-04-09 06:16:49
    ## 76  uuid:77b3021b-a9d6-4276-aaeb-5bfcfd413852 2017-04-09 06:35:16
    ## 77  uuid:2186e2ec-f65a-47cc-9bc1-a0f36dd9591c 2017-04-09 06:54:49
    ## 78  uuid:87998c33-c8d2-49ec-9dae-c123735957ec 2017-04-09 07:59:49
    ## 79  uuid:ece89122-ea99-4378-b67e-a170127ec4e6 2017-04-09 08:23:05
    ## 80  uuid:bf373763-dca5-4906-901b-d1bacb4f0286 2017-04-09 08:43:08
    ## 81  uuid:394033e8-a6e2-4e39-bfac-458753a1ed78 2017-04-09 09:08:04
    ## 82  uuid:268bfd97-991c-473f-bd51-bc80676c65c6 2017-04-09 15:20:26
    ## 83  uuid:0a42c9ee-a840-4dda-8123-15c1bede5dfc 2017-04-09 15:48:14
    ## 84  uuid:2c132929-9c8f-450a-81ff-367360ce2c19 2017-04-09 16:13:19
    ## 85  uuid:44e427d1-a448-4bf2-b529-7d67b2266c06 2017-04-09 18:00:41
    ## 86  uuid:85c99fd2-775f-40c9-8654-68223f59d091 2017-04-09 18:32:09
    ## 87  uuid:28c64954-739c-444c-a6e0-355878e471c8 2017-04-09 19:15:21
    ## 88  uuid:9e79a31c-3ea5-44f0-80f9-a32db49422e3 2017-04-09 19:31:47
    ## 89  uuid:06d39051-38ef-4757-b68b-3327b1f16b9d 2017-04-09 19:48:09
    ## 90  uuid:c4a2c982-244e-45a5-aa4b-71fa53f99e18 2017-04-26 15:46:24
    ## 91  uuid:ac3da862-9e6c-4962-94b6-f4c31624f207 2017-04-26 16:13:50
    ## 92  uuid:4178a296-903a-4a8e-9cfa-0cd6143476e8 2017-04-26 16:45:28
    ## 93  uuid:a1e9df00-c8ae-411c-931c-c7df898c68d0 2017-04-27 12:27:31
    ## 94  uuid:4d0f472b-f8ae-4026-87c9-6b5be14b0a70 2017-04-27 12:58:02
    ## 95  uuid:b3b309c6-f234-4830-8b30-87d26a17ee1d 2017-04-27 16:11:23
    ## 96  uuid:3c174acd-e431-4523-9ad6-eb14cddca805 2017-04-27 16:42:02
    ## 97  uuid:e9d79844-ef14-493b-bbd6-d13691cc660e 2017-04-27 17:38:53
    ## 98  uuid:76206b0b-af74-4344-b24f-81e839f0d7b0 2017-04-28 06:27:07
    ## 99  uuid:da3fa7cc-5ce9-44fd-9a78-b8982b607515 2017-04-28 07:09:39
    ## 100 uuid:a85df6df-0336-46fa-a9f4-522bf6f8b438 2017-04-28 09:01:47
    ## 101 uuid:bb2bb365-7d7d-4fe9-9353-b21269676119 2017-04-28 14:25:13
    ## 102 uuid:af0904ee-4fdb-4090-973f-599c81ddf022 2017-04-28 15:32:38
    ## 103 uuid:468797c1-4a65-4f35-9c83-e28ce46972a2 2017-04-30 05:51:18
    ## 104 uuid:602cd3f6-4a97-49c6-80e3-bcfd5c78dfa4 2017-05-03 13:14:43
    ## 105 uuid:e7c51ac4-24e4-475e-88e7-f85e896945e3 2017-05-03 13:37:57
    ## 106 uuid:01210861-aba1-4268-98d0-0260e05f5155 2017-05-03 14:00:13
    ## 107 uuid:77335b2e-8812-4a35-b1e5-ca9ab626dfea 2017-05-04 10:26:35
    ## 108 uuid:02b05c68-302e-4e7a-b229-81cb1377fd29 2017-05-04 10:47:05
    ## 109 uuid:fa201fce-4e94-44b8-b435-c558c2e1ed55 2017-05-04 11:16:57
    ## 110 uuid:628fe23d-188f-43e4-a203-a4bf3257d461 2017-05-11 05:24:25
    ## 111 uuid:e4f4d6ba-e698-45a5-947f-ba6da88cc22b 2017-05-11 05:42:08
    ## 112 uuid:cfee6297-2c0e-4f8a-94cc-9aaee0bd64cb 2017-05-11 06:09:56
    ## 113 uuid:3fe626b3-c794-48e1-a80f-5bfe440c507b 2017-05-11 06:28:02
    ## 114 uuid:0670cef6-d233-4852-89d8-36955261b0a3 2017-05-18 04:36:23
    ## 115 uuid:9a096a12-b335-468c-b3cc-1191180d62de 2017-05-18 05:55:04
    ## 116 uuid:92613d0d-e7b1-4d62-8ea4-451d7cd0a982 2017-05-18 10:37:37
    ## 117 uuid:37577f91-d665-443e-8d70-b914954cef4b 2017-05-18 10:56:16
    ## 118 uuid:f22831ec-6bc3-4b73-9197-4b01e01abb66 2017-06-03 05:08:49
    ## 119 uuid:62f3f7af-f0f3-4f88-b9e0-acf8baa49ae4 2017-06-03 05:32:33
    ## 120 uuid:40aac732-94df-496c-97ba-5b67f59bcc7a 2017-06-03 05:53:28
    ## 121 uuid:a9d1a013-043b-475d-a71b-77ed80abe970 2017-06-03 06:25:09
    ## 122 uuid:43ec6132-478c-4f87-878d-fb3c0c4d0c74 2017-06-03 06:50:47
    ## 123 uuid:64fc743e-8176-40f6-8ae4-36ae97fac1d9 2017-06-03 07:21:48
    ## 124 uuid:c17e374c-280b-4e78-bf21-74a7c1c73492 2017-06-03 15:23:01
    ## 125 uuid:dad53aff-b520-4015-a9e3-f5fdf9168fe1 2017-06-03 15:54:03
    ## 126 uuid:f94409a6-e461-4e4c-a6fb-0072d3d58b00 2017-06-03 16:17:55
    ## 127 uuid:69caea81-a4e5-4e8d-83cd-9c18d8e8d965 2017-05-18 04:13:37
    ## 128 uuid:5ccc2e5a-ea90-48b5-8542-69400d5334df 2017-06-04 09:36:20
    ## 129 uuid:95c11a30-d44f-40c4-8ea8-ec34fca6bbbf 2017-06-04 10:13:36
    ## 130 uuid:ffc83162-ff24-4a87-8709-eff17abc0b3b 2017-06-04 10:33:55
    ## 131 uuid:aa77a0d7-7142-41c8-b494-483a5b68d8a7 2017-06-04 10:52:46
    ##               end_clean
    ## 1   2017-04-02 17:29:08
    ## 2   2017-04-02 17:26:19
    ## 3   2017-04-02 17:26:53
    ## 4   2017-04-02 17:27:16
    ## 5   2017-04-02 17:27:35
    ## 6   2017-04-02 17:28:02
    ## 7   2017-04-02 17:28:19
    ## 8   2017-04-02 17:28:39
    ## 9   2017-04-02 16:42:08
    ## 10  2017-04-02 17:25:11
    ## 11  2017-04-03 03:31:10
    ## 12  2017-04-03 03:58:34
    ## 13  2017-04-03 04:19:36
    ## 14  2017-04-03 04:50:05
    ## 15  2017-04-03 05:28:44
    ## 16  2017-04-03 05:40:53
    ## 17  2017-04-03 05:57:57
    ## 18  2017-04-03 12:39:48
    ## 19  2017-04-03 12:53:29
    ## 20  2017-04-03 14:20:04
    ## 21  2017-04-03 14:44:39
    ## 22  2017-04-03 16:40:47
    ## 23  2017-04-03 17:04:28
    ## 24  2017-04-03 17:43:01
    ## 25  2017-04-04 04:29:47
    ## 26  2017-04-04 04:44:19
    ## 27  2017-04-05 05:14:45
    ## 28  2017-04-05 05:36:18
    ## 29  2017-04-05 06:05:44
    ## 30  2017-04-05 06:20:39
    ## 31  2017-04-05 06:38:26
    ## 32  2017-04-05 08:05:32
    ## 33  2017-04-05 08:25:48
    ## 34  2017-04-05 16:21:59
    ## 35  2017-04-05 16:50:25
    ## 36  2017-04-05 17:10:53
    ## 37  2017-04-05 17:26:51
    ## 38  2017-04-05 17:50:57
    ## 39  2017-04-06 08:44:47
    ## 40  2017-04-06 09:03:47
    ## 41  2017-04-06 09:14:05
    ## 42  2017-04-06 09:30:54
    ## 43  2017-04-06 09:53:53
    ## 44  2017-04-06 14:53:01
    ## 45  2017-04-06 15:11:57
    ## 46  2017-04-06 15:45:32
    ## 47  2017-04-07 14:19:45
    ## 48  2017-04-07 14:40:23
    ## 49  2017-04-07 14:55:51
    ## 50  2017-04-07 15:26:23
    ## 51  2017-04-07 15:39:10
    ## 52  2017-04-08 05:02:58
    ## 53  2017-04-08 05:33:51
    ## 54  2017-04-08 05:52:15
    ## 55  2017-04-08 06:05:41
    ## 56  2017-04-08 06:26:12
    ## 57  2017-04-08 06:39:40
    ## 58  2017-04-08 08:48:51
    ## 59  2017-04-08 09:02:34
    ## 60  2017-04-08 09:20:18
    ## 61  2017-04-08 11:14:09
    ## 62  2017-04-08 13:41:21
    ## 63  2017-04-08 13:52:07
    ## 64  2017-04-08 14:02:24
    ## 65  2017-04-08 14:15:45
    ## 66  2017-04-08 21:33:45
    ## 67  2017-04-08 21:49:02
    ## 68  2017-04-09 22:06:57
    ## 69  2017-04-09 22:21:08
    ## 70  2017-04-09 22:40:57
    ## 71  2017-04-09 15:19:22
    ## 72  2017-04-09 05:27:41
    ## 73  2017-04-09 05:43:51
    ## 74  2017-04-09 06:16:11
    ## 75  2017-04-09 06:28:48
    ## 76  2017-04-09 06:48:01
    ## 77  2017-04-09 07:14:16
    ## 78  2017-04-09 08:22:34
    ## 79  2017-04-09 08:42:02
    ## 80  2017-04-09 09:07:48
    ## 81  2017-04-09 09:34:12
    ## 82  2017-04-09 15:46:14
    ## 83  2017-04-09 16:12:46
    ## 84  2017-04-09 16:35:24
    ## 85  2017-04-09 18:31:40
    ## 86  2017-04-09 19:14:52
    ## 87  2017-04-09 19:27:56
    ## 88  2017-04-09 19:45:38
    ## 89  2017-04-09 20:08:15
    ## 90  2017-04-26 16:13:33
    ## 91  2017-04-26 16:45:01
    ## 92  2017-04-26 17:26:21
    ## 93  2017-04-27 12:56:42
    ## 94  2017-04-27 13:23:06
    ## 95  2017-04-27 16:41:41
    ## 96  2017-04-27 18:11:54
    ## 97  2017-04-27 18:09:45
    ## 98  2017-04-28 06:52:04
    ## 99  2017-04-28 07:31:38
    ## 100 2017-04-28 09:25:51
    ## 101 2017-04-28 15:18:10
    ## 102 2017-04-28 15:58:10
    ## 103 2017-04-30 06:47:01
    ## 104 2017-05-03 13:37:53
    ## 105 2017-05-03 13:58:06
    ## 106 2017-05-03 14:27:03
    ## 107 2017-05-04 10:46:35
    ## 108 2017-05-04 11:16:05
    ## 109 2017-05-04 11:38:38
    ## 110 2017-05-11 05:41:56
    ## 111 2017-05-11 06:08:58
    ## 112 2017-05-11 06:22:19
    ## 113 2017-05-11 06:55:35
    ## 114 2017-05-18 05:02:38
    ## 115 2017-05-18 06:37:10
    ## 116 2017-05-18 10:56:00
    ## 117 2017-05-18 11:07:35
    ## 118 2017-06-03 05:32:19
    ## 119 2017-06-03 05:51:49
    ## 120 2017-06-03 06:25:06
    ## 121 2017-06-03 06:45:06
    ## 122 2017-06-03 07:20:21
    ## 123 2017-06-03 07:51:29
    ## 124 2017-06-03 15:53:10
    ## 125 2017-06-03 16:17:26
    ## 126 2017-06-03 17:16:39
    ## 127 2017-05-18 04:35:47
    ## 128 2017-06-04 10:13:32
    ## 129 2017-06-04 10:32:06
    ## 130 2017-06-04 10:52:22
    ## 131 2017-06-04 11:08:13

2.  Create a column in the dataset called `duration`. This column should
    be the length of the interview in **hours**.

Hint: See section 16.4.1 Durations in the R for Data Science text for
information on durations in R. Functions `as.duration()` and `dhours()`
will be helpful.

``` r
test1 <- new_interview %>% 
  mutate(duration = round(as.duration(new_end - new_start)/dhours(1),2)) %>% 
  select(duration, everything())
colnames(test1)[1]="duration (hours)"
test1 
```

    ##     duration (hours)           new_start             new_end
    ## 1             247.65 2017-03-23 09:49:57 2017-04-02 17:29:08
    ## 2               7.63 2017-04-02 09:48:16 2017-04-02 17:26:19
    ## 3               2.86 2017-04-02 14:35:26 2017-04-02 17:26:53
    ## 4               2.53 2017-04-02 14:55:18 2017-04-02 17:27:16
    ## 5               2.28 2017-04-02 15:10:35 2017-04-02 17:27:35
    ## 6               2.01 2017-04-02 15:27:25 2017-04-02 17:28:02
    ## 7               1.84 2017-04-02 15:38:01 2017-04-02 17:28:19
    ## 8               1.48 2017-04-02 15:59:52 2017-04-02 17:28:39
    ## 9               0.31 2017-04-02 16:23:36 2017-04-02 16:42:08
    ## 10              0.36 2017-04-02 17:03:28 2017-04-02 17:25:11
    ## 11              0.25 2017-04-03 03:16:15 2017-04-03 03:31:10
    ## 12              0.46 2017-04-03 03:31:13 2017-04-03 03:58:34
    ## 13              0.35 2017-04-03 03:58:43 2017-04-03 04:19:36
    ## 14              0.50 2017-04-03 04:19:57 2017-04-03 04:50:05
    ## 15              0.27 2017-04-03 05:12:17 2017-04-03 05:28:44
    ## 16              0.19 2017-04-03 05:29:24 2017-04-03 05:40:53
    ## 17              0.27 2017-04-03 05:41:42 2017-04-03 05:57:57
    ## 18              0.21 2017-04-03 12:27:04 2017-04-03 12:39:48
    ## 19              0.22 2017-04-03 12:40:14 2017-04-03 12:53:29
    ## 20              0.25 2017-04-03 14:04:50 2017-04-03 14:20:04
    ## 21              0.33 2017-04-03 14:24:58 2017-04-03 14:44:39
    ## 22              0.20 2017-04-03 16:28:52 2017-04-03 16:40:47
    ## 23              0.39 2017-04-03 16:41:04 2017-04-03 17:04:28
    ## 24              0.39 2017-04-03 17:19:49 2017-04-03 17:43:01
    ## 25              0.46 2017-04-04 04:01:58 2017-04-04 04:29:47
    ## 26              0.23 2017-04-04 04:30:19 2017-04-04 04:44:19
    ## 27              0.25 2017-04-05 04:59:42 2017-04-05 05:14:45
    ## 28              0.36 2017-04-05 05:14:49 2017-04-05 05:36:18
    ## 29              0.47 2017-04-05 05:37:30 2017-04-05 06:05:44
    ## 30              0.24 2017-04-05 06:05:58 2017-04-05 06:20:39
    ## 31              0.28 2017-04-05 06:21:20 2017-04-05 06:38:26
    ## 32              1.44 2017-04-05 06:38:55 2017-04-05 08:05:32
    ## 33              0.29 2017-04-05 08:08:19 2017-04-05 08:25:48
    ## 34              0.35 2017-04-05 16:00:47 2017-04-05 16:21:59
    ## 35              0.47 2017-04-05 16:22:13 2017-04-05 16:50:25
    ## 36              0.33 2017-04-05 16:50:48 2017-04-05 17:10:53
    ## 37              0.15 2017-04-05 17:17:48 2017-04-05 17:26:51
    ## 38              0.38 2017-04-05 17:28:12 2017-04-05 17:50:57
    ## 39              0.22 2017-04-06 08:31:17 2017-04-06 08:44:47
    ## 40              0.32 2017-04-06 08:44:51 2017-04-06 09:03:47
    ## 41              0.17 2017-04-06 09:03:50 2017-04-06 09:14:05
    ## 42              0.28 2017-04-06 09:14:22 2017-04-06 09:30:54
    ## 43              0.37 2017-04-06 09:31:56 2017-04-06 09:53:53
    ## 44              0.14 2017-04-06 14:44:32 2017-04-06 14:53:01
    ## 45              0.31 2017-04-06 14:53:04 2017-04-06 15:11:57
    ## 46              0.43 2017-04-06 15:19:41 2017-04-06 15:45:32
    ## 47              0.24 2017-04-07 14:05:25 2017-04-07 14:19:45
    ## 48              0.34 2017-04-07 14:19:49 2017-04-07 14:40:23
    ## 49              0.21 2017-04-07 14:43:09 2017-04-07 14:55:51
    ## 50              0.51 2017-04-07 14:56:01 2017-04-07 15:26:23
    ## 51              0.19 2017-04-07 15:27:45 2017-04-07 15:39:10
    ## 52              0.31 2017-04-08 04:44:09 2017-04-08 05:02:58
    ## 53              0.51 2017-04-08 05:03:08 2017-04-08 05:33:51
    ## 54              0.26 2017-04-08 05:36:55 2017-04-08 05:52:15
    ## 55              0.22 2017-04-08 05:52:32 2017-04-08 06:05:41
    ## 56              0.34 2017-04-08 06:05:59 2017-04-08 06:26:12
    ## 57              0.22 2017-04-08 06:26:22 2017-04-08 06:39:40
    ## 58              0.38 2017-04-08 08:25:49 2017-04-08 08:48:51
    ## 59              0.17 2017-04-08 08:52:05 2017-04-08 09:02:34
    ## 60              0.29 2017-04-08 09:03:01 2017-04-08 09:20:18
    ## 61              0.45 2017-04-08 10:47:11 2017-04-08 11:14:09
    ## 62              0.22 2017-04-08 13:27:58 2017-04-08 13:41:21
    ## 63              0.17 2017-04-08 13:41:39 2017-04-08 13:52:07
    ## 64              0.16 2017-04-08 13:52:30 2017-04-08 14:02:24
    ## 65              0.22 2017-04-08 14:02:49 2017-04-08 14:15:45
    ## 66              0.40 2017-04-08 21:09:38 2017-04-08 21:33:45
    ## 67              0.24 2017-04-08 21:34:23 2017-04-08 21:49:02
    ## 68             24.29 2017-04-08 21:49:40 2017-04-09 22:06:57
    ## 69              0.22 2017-04-09 22:08:07 2017-04-09 22:21:08
    ## 70              0.33 2017-04-09 22:21:23 2017-04-09 22:40:57
    ## 71              0.32 2017-04-09 15:00:19 2017-04-09 15:19:22
    ## 72              0.19 2017-04-09 05:16:06 2017-04-09 05:27:41
    ## 73              0.27 2017-04-09 05:27:46 2017-04-09 05:43:51
    ## 74              0.48 2017-04-09 05:47:31 2017-04-09 06:16:11
    ## 75              0.20 2017-04-09 06:16:49 2017-04-09 06:28:48
    ## 76              0.21 2017-04-09 06:35:16 2017-04-09 06:48:01
    ## 77              0.32 2017-04-09 06:54:49 2017-04-09 07:14:16
    ## 78              0.38 2017-04-09 07:59:49 2017-04-09 08:22:34
    ## 79              0.32 2017-04-09 08:23:05 2017-04-09 08:42:02
    ## 80              0.41 2017-04-09 08:43:08 2017-04-09 09:07:48
    ## 81              0.44 2017-04-09 09:08:04 2017-04-09 09:34:12
    ## 82              0.43 2017-04-09 15:20:26 2017-04-09 15:46:14
    ## 83              0.41 2017-04-09 15:48:14 2017-04-09 16:12:46
    ## 84              0.37 2017-04-09 16:13:19 2017-04-09 16:35:24
    ## 85              0.52 2017-04-09 18:00:41 2017-04-09 18:31:40
    ## 86              0.71 2017-04-09 18:32:09 2017-04-09 19:14:52
    ## 87              0.21 2017-04-09 19:15:21 2017-04-09 19:27:56
    ## 88              0.23 2017-04-09 19:31:47 2017-04-09 19:45:38
    ## 89              0.34 2017-04-09 19:48:09 2017-04-09 20:08:15
    ## 90              0.45 2017-04-26 15:46:24 2017-04-26 16:13:33
    ## 91              0.52 2017-04-26 16:13:50 2017-04-26 16:45:01
    ## 92              0.68 2017-04-26 16:45:28 2017-04-26 17:26:21
    ## 93              0.49 2017-04-27 12:27:31 2017-04-27 12:56:42
    ## 94              0.42 2017-04-27 12:58:02 2017-04-27 13:23:06
    ## 95              0.50 2017-04-27 16:11:23 2017-04-27 16:41:41
    ## 96              1.50 2017-04-27 16:42:02 2017-04-27 18:11:54
    ## 97              0.51 2017-04-27 17:38:53 2017-04-27 18:09:45
    ## 98              0.42 2017-04-28 06:27:07 2017-04-28 06:52:04
    ## 99              0.37 2017-04-28 07:09:39 2017-04-28 07:31:38
    ## 100             0.40 2017-04-28 09:01:47 2017-04-28 09:25:51
    ## 101             0.88 2017-04-28 14:25:13 2017-04-28 15:18:10
    ## 102             0.43 2017-04-28 15:32:38 2017-04-28 15:58:10
    ## 103             0.93 2017-04-30 05:51:18 2017-04-30 06:47:01
    ## 104             0.39 2017-05-03 13:14:43 2017-05-03 13:37:53
    ## 105             0.34 2017-05-03 13:37:57 2017-05-03 13:58:06
    ## 106             0.45 2017-05-03 14:00:13 2017-05-03 14:27:03
    ## 107             0.33 2017-05-04 10:26:35 2017-05-04 10:46:35
    ## 108             0.48 2017-05-04 10:47:05 2017-05-04 11:16:05
    ## 109             0.36 2017-05-04 11:16:57 2017-05-04 11:38:38
    ## 110             0.29 2017-05-11 05:24:25 2017-05-11 05:41:56
    ## 111             0.45 2017-05-11 05:42:08 2017-05-11 06:08:58
    ## 112             0.21 2017-05-11 06:09:56 2017-05-11 06:22:19
    ## 113             0.46 2017-05-11 06:28:02 2017-05-11 06:55:35
    ## 114             0.44 2017-05-18 04:36:23 2017-05-18 05:02:38
    ## 115             0.70 2017-05-18 05:55:04 2017-05-18 06:37:10
    ## 116             0.31 2017-05-18 10:37:37 2017-05-18 10:56:00
    ## 117             0.19 2017-05-18 10:56:16 2017-05-18 11:07:35
    ## 118             0.39 2017-06-03 05:08:49 2017-06-03 05:32:19
    ## 119             0.32 2017-06-03 05:32:33 2017-06-03 05:51:49
    ## 120             0.53 2017-06-03 05:53:28 2017-06-03 06:25:06
    ## 121             0.33 2017-06-03 06:25:09 2017-06-03 06:45:06
    ## 122             0.49 2017-06-03 06:50:47 2017-06-03 07:20:21
    ## 123             0.49 2017-06-03 07:21:48 2017-06-03 07:51:29
    ## 124             0.50 2017-06-03 15:23:01 2017-06-03 15:53:10
    ## 125             0.39 2017-06-03 15:54:03 2017-06-03 16:17:26
    ## 126             0.98 2017-06-03 16:17:55 2017-06-03 17:16:39
    ## 127             0.37 2017-05-18 04:13:37 2017-05-18 04:35:47
    ## 128             0.62 2017-06-04 09:36:20 2017-06-04 10:13:32
    ## 129             0.31 2017-06-04 10:13:36 2017-06-04 10:32:06
    ## 130             0.31 2017-06-04 10:33:55 2017-06-04 10:52:22
    ## 131             0.26 2017-06-04 10:52:46 2017-06-04 11:08:13
    ##                   start                 end  id   interview_date quest_no
    ## 1   2017-03-23 09:49:57 2017-04-02 17:29:08   1 17 November 2016        1
    ## 2   2017-04-02 09:48:16 2017-04-02 17:26:19   2 17 November 2016        1
    ## 3   2017-04-02 14:35:26 2017-04-02 17:26:53   3 17 November 2016        3
    ## 4   2017-04-02 14:55:18 2017-04-02 17:27:16   4 17 November 2016        4
    ## 5   2017-04-02 15:10:35 2017-04-02 17:27:35   5 17 November 2016        5
    ## 6   2017-04-02 15:27:25 2017-04-02 17:28:02   6 17 November 2016        6
    ## 7   2017-04-02 15:38:01 2017-04-02 17:28:19   7 17 November 2016        7
    ## 8   2017-04-02 15:59:52 2017-04-02 17:28:39   8 16 November 2016        8
    ## 9   2017-04-02 16:23:36 2017-04-02 16:42:08   9 16 November 2016        9
    ## 10  2017-04-02 17:03:28 2017-04-02 17:25:11  10 16 December 2016       10
    ## 11  2017-04-03 03:16:15 2017-04-03 03:31:10  11 21 November 2016       11
    ## 12  2017-04-03 03:31:13 2017-04-03 03:58:34  12 21 November 2016       12
    ## 13  2017-04-03 03:58:43 2017-04-03 04:19:36  13 21 November 2016       13
    ## 14  2017-04-03 04:19:57 2017-04-03 04:50:05  14 21 November 2016       14
    ## 15  2017-04-03 05:12:17 2017-04-03 05:28:44  15 21 November 2016       15
    ## 16  2017-04-03 05:29:24 2017-04-03 05:40:53  16 24 November 2016       16
    ## 17  2017-04-03 05:41:42 2017-04-03 05:57:57  17 21 November 2016       17
    ## 18  2017-04-03 12:27:04 2017-04-03 12:39:48  18 21 November 2016       18
    ## 19  2017-04-03 12:40:14 2017-04-03 12:53:29  19 21 November 2016       19
    ## 20  2017-04-03 14:04:50 2017-04-03 14:20:04  20 21 November 2016       20
    ## 21  2017-04-03 14:24:58 2017-04-03 14:44:39  21 21 November 2016       21
    ## 22  2017-04-03 16:28:52 2017-04-03 16:40:47  22 21 November 2016       22
    ## 23  2017-04-03 16:41:04 2017-04-03 17:04:28  23 21 November 2016       23
    ## 24  2017-04-03 17:19:49 2017-04-03 17:43:01  24 21 November 2016       24
    ## 25  2017-04-04 04:01:58 2017-04-04 04:29:47  25 21 November 2016       25
    ## 26  2017-04-04 04:30:19 2017-04-04 04:44:19  26 21 November 2016       26
    ## 27  2017-04-05 04:59:42 2017-04-05 05:14:45  27 21 November 2016       27
    ## 28  2017-04-05 05:14:49 2017-04-05 05:36:18  28 21 November 2016       28
    ## 29  2017-04-05 05:37:30 2017-04-05 06:05:44  29 21 November 2016       29
    ## 30  2017-04-05 06:05:58 2017-04-05 06:20:39  30 21 November 2016       30
    ## 31  2017-04-05 06:21:20 2017-04-05 06:38:26  31 21 November 2016       31
    ## 32  2017-04-05 06:38:55 2017-04-05 08:05:32  32 21 November 2016       32
    ## 33  2017-04-05 08:08:19 2017-04-05 08:25:48  33 21 November 2016       33
    ## 34  2017-04-05 16:00:47 2017-04-05 16:21:59  34 17 November 2016       34
    ## 35  2017-04-05 16:22:13 2017-04-05 16:50:25  35 17 November 2016       35
    ## 36  2017-04-05 16:50:48 2017-04-05 17:10:53  36 17 November 2016       36
    ## 37  2017-04-05 17:17:48 2017-04-05 17:26:51  37 17 November 2016       37
    ## 38  2017-04-05 17:28:12 2017-04-05 17:50:57  38 17 November 2016       38
    ## 39  2017-04-06 08:31:17 2017-04-06 08:44:47  39 17 November 2016       39
    ## 40  2017-04-06 08:44:51 2017-04-06 09:03:47  40 17 November 2016       40
    ## 41  2017-04-06 09:03:50 2017-04-06 09:14:05  41 17 November 2016       41
    ## 42  2017-04-06 09:14:22 2017-04-06 09:30:54  42 17 November 2016       42
    ## 43  2017-04-06 09:31:56 2017-04-06 09:53:53  43 17 November 2016       43
    ## 44  2017-04-06 14:44:32 2017-04-06 14:53:01  44 17 November 2016       44
    ## 45  2017-04-06 14:53:04 2017-04-06 15:11:57  45 17 November 2016       45
    ## 46  2017-04-06 15:19:41 2017-04-06 15:45:32  46 17 November 2016       46
    ## 47  2017-04-07 14:05:25 2017-04-07 14:19:45  47 17 November 2016       47
    ## 48  2017-04-07 14:19:49 2017-04-07 14:40:23  48 16 November 2016       48
    ## 49  2017-04-07 14:43:09 2017-04-07 14:55:51  49 16 November 2016       49
    ## 50  2017-04-07 14:56:01 2017-04-07 15:26:23  50 16 November 2016       50
    ## 51  2017-04-07 15:27:45 2017-04-07 15:39:10  51 16 November 2016       51
    ## 52  2017-04-08 04:44:09 2017-04-08 05:02:58  52 16 November 2016       52
    ## 53  2017-04-08 05:03:08 2017-04-08 05:33:51  53 16 November 2016       21
    ## 54  2017-04-08 05:36:55 2017-04-08 05:52:15  54 16 November 2016       54
    ## 55  2017-04-08 05:52:32 2017-04-08 06:05:41  55 16 November 2016       55
    ## 56  2017-04-08 06:05:59 2017-04-08 06:26:12  56 16 November 2016       56
    ## 57  2017-04-08 06:26:22 2017-04-08 06:39:40  57 16 November 2016       57
    ## 58  2017-04-08 08:25:49 2017-04-08 08:48:51  58 16 November 2016       58
    ## 59  2017-04-08 08:52:05 2017-04-08 09:02:34  59 16 November 2016       59
    ## 60  2017-04-08 09:03:01 2017-04-08 09:20:18  60 16 November 2016       60
    ## 61  2017-04-08 10:47:11 2017-04-08 11:14:09  61 16 November 2016       61
    ## 62  2017-04-08 13:27:58 2017-04-08 13:41:21  62 16 November 2016       62
    ## 63  2017-04-08 13:41:39 2017-04-08 13:52:07  63 16 November 2016       63
    ## 64  2017-04-08 13:52:30 2017-04-08 14:02:24  64 16 November 2016       64
    ## 65  2017-04-08 14:02:49 2017-04-08 14:15:45  65 16 November 2016       65
    ## 66  2017-04-08 21:09:38 2017-04-08 21:33:45  66 16 November 2016       66
    ## 67  2017-04-08 21:34:23 2017-04-08 21:49:02  67 16 November 2016       67
    ## 68  2017-04-08 21:49:40 2017-04-09 22:06:57  68 16 November 2016       68
    ## 69  2017-04-09 22:08:07 2017-04-09 22:21:08  69 16 November 2016       69
    ## 70  2017-04-09 22:21:23 2017-04-09 22:40:57  70 16 November 2016       70
    ## 71  2017-04-09 15:00:19 2017-04-09 15:19:22  71 18 November 2016       71
    ## 72  2017-04-09 05:16:06 2017-04-09 05:27:41  72 16 November 2016      127
    ## 73  2017-04-09 05:27:46 2017-04-09 05:43:51  73 23 November 2016      133
    ## 74  2017-04-09 05:47:31 2017-04-09 06:16:11  74 24 November 2016      152
    ## 75  2017-04-09 06:16:49 2017-04-09 06:28:48  75 24 November 2016      153
    ## 76  2017-04-09 06:35:16 2017-04-09 06:48:01  76 24 November 2016      155
    ## 77  2017-04-09 06:54:49 2017-04-09 07:14:16  77 25 November 2016      178
    ## 78  2017-04-09 07:59:49 2017-04-09 08:22:34  78 25 November 2016      177
    ## 79  2017-04-09 08:23:05 2017-04-09 08:42:02  79 25 November 2016      180
    ## 80  2017-04-09 08:43:08 2017-04-09 09:07:48  80 25 November 2016      181
    ## 81  2017-04-09 09:08:04 2017-04-09 09:34:12  81 25 November 2016      182
    ## 82  2017-04-09 15:20:26 2017-04-09 15:46:14  82 28 November 2016      186
    ## 83  2017-04-09 15:48:14 2017-04-09 16:12:46  83 28 November 2016      187
    ## 84  2017-04-09 16:13:19 2017-04-09 16:35:24  84 28 November 2016      195
    ## 85  2017-04-09 18:00:41 2017-04-09 18:31:40  85 28 November 2016      196
    ## 86  2017-04-09 18:32:09 2017-04-09 19:14:52  86 28 November 2016      197
    ## 87  2017-04-09 19:15:21 2017-04-09 19:27:56  87 28 November 2016      198
    ## 88  2017-04-09 19:31:47 2017-04-09 19:45:38  88 21 November 2016      201
    ## 89  2017-04-09 19:48:09 2017-04-09 20:08:15  89 17 November 2016      202
    ## 90  2017-04-26 15:46:24 2017-04-26 16:13:33  90    26 April 2017       72
    ## 91  2017-04-26 16:13:50 2017-04-26 16:45:01  91    26 April 2017       73
    ## 92  2017-04-26 16:45:28 2017-04-26 17:26:21  92    26 April 2017       76
    ## 93  2017-04-27 12:27:31 2017-04-27 12:56:42  93    27 April 2017       83
    ## 94  2017-04-27 12:58:02 2017-04-27 13:23:06  94    27 April 2017       85
    ## 95  2017-04-27 16:11:23 2017-04-27 16:41:41  95    27 April 2017       89
    ## 96  2017-04-27 16:42:02 2017-04-27 18:11:54  96    27 April 2017      101
    ## 97  2017-04-27 17:38:53 2017-04-27 18:09:45  97    27 April 2017      103
    ## 98  2017-04-28 06:27:07 2017-04-28 06:52:04  98    28 April 2017      102
    ## 99  2017-04-28 07:09:39 2017-04-28 07:31:38  99    28 April 2017       78
    ## 100 2017-04-28 09:01:47 2017-04-28 09:25:51 100    28 April 2017       80
    ## 101 2017-04-28 14:25:13 2017-04-28 15:18:10 101    28 April 2017      104
    ## 102 2017-04-28 15:32:38 2017-04-28 15:58:10 102    28 April 2017      105
    ## 103 2017-04-30 05:51:18 2017-04-30 06:47:01 103    30 April 2017      106
    ## 104 2017-05-03 13:14:43 2017-05-03 13:37:53 104      03 May 2017      109
    ## 105 2017-05-03 13:37:57 2017-05-03 13:58:06 105      03 May 2017      110
    ## 106 2017-05-03 14:00:13 2017-05-03 14:27:03 106      03 May 2017      113
    ## 107 2017-05-04 10:26:35 2017-05-04 10:46:35 107      04 May 2017      118
    ## 108 2017-05-04 10:47:05 2017-05-04 11:16:05 108      04 May 2017      125
    ## 109 2017-05-04 11:16:57 2017-05-04 11:38:38 109      04 May 2017      119
    ## 110 2017-05-11 05:24:25 2017-05-11 05:41:56 110      11 May 2017      115
    ## 111 2017-05-11 05:42:08 2017-05-11 06:08:58 111      11 May 2017      108
    ## 112 2017-05-11 06:09:56 2017-05-11 06:22:19 112      11 May 2017      116
    ## 113 2017-05-11 06:28:02 2017-05-11 06:55:35 113      11 May 2017      117
    ## 114 2017-05-18 04:36:23 2017-05-18 05:02:38 114      18 May 2017      144
    ## 115 2017-05-18 05:55:04 2017-05-18 06:37:10 115      18 May 2017      143
    ## 116 2017-05-18 10:37:37 2017-05-18 10:56:00 116      18 May 2017      150
    ## 117 2017-05-18 10:56:16 2017-05-18 11:07:35 117      18 May 2017      159
    ## 118 2017-06-03 05:08:49 2017-06-03 05:32:19 118     03 June 2017      160
    ## 119 2017-06-03 05:32:33 2017-06-03 05:51:49 119     03 June 2017      165
    ## 120 2017-06-03 05:53:28 2017-06-03 06:25:06 120     03 June 2017      166
    ## 121 2017-06-03 06:25:09 2017-06-03 06:45:06 121     03 June 2017      167
    ## 122 2017-06-03 06:50:47 2017-06-03 07:20:21 122     03 June 2017      174
    ## 123 2017-06-03 07:21:48 2017-06-03 07:51:29 123     03 June 2017      175
    ## 124 2017-06-03 15:23:01 2017-06-03 15:53:10 124     03 June 2017      189
    ## 125 2017-06-03 15:54:03 2017-06-03 16:17:26 125     03 June 2017      191
    ## 126 2017-06-03 16:17:55 2017-06-03 17:16:39 126     03 June 2017      192
    ## 127 2017-05-18 04:13:37 2017-05-18 04:35:47 127      18 May 2017      126
    ## 128 2017-06-04 09:36:20 2017-06-04 10:13:32 128     04 June 2017      193
    ## 129 2017-06-04 10:13:36 2017-06-04 10:32:06 129     04 June 2017      194
    ## 130 2017-06-04 10:33:55 2017-06-04 10:52:22 130     04 June 2017      199
    ## 131 2017-06-04 10:52:46 2017-06-04 11:08:13 131     04 June 2017      200
    ##     province district    ward           village years_farm agr_assoc  te2
    ## 1     Manica   Manica Bandula               God         11        no NULL
    ## 2     Manica   Manica Bandula               God          2       yes NULL
    ## 3     Manica   Manica Bandula               God         40        no NULL
    ## 4     Manica   Manica Bandula               God          6        no NULL
    ## 5     Manica   Manica Bandula               God         18        no NULL
    ## 6     Manica   Manica Bandula               God          3        no NULL
    ## 7     Manica   Manica Bandula               God         20        no NULL
    ## 8     Manica   Manica  Manica          Chirodzo         16       yes NULL
    ## 9     Manica   Manica Bandula          Chirodzo         16        no NULL
    ## 10    Manica   Manica Bandula          Chirodzo         22        no NULL
    ## 11    Manica   Manica Bandula               God          6        no NULL
    ## 12    Manica   Manica Bandula               God         20        no NULL
    ## 13    Manica   Manica Bandula               God          7       yes NULL
    ## 14    Manica   Manica Bandula               God         20       yes NULL
    ## 15    Manica   Manica Bandula               God         30       yes NULL
    ## 16    Manica   Manica Bandula               God         24       yes NULL
    ## 17    Manica   Manica Bandula               God         10       yes NULL
    ## 18    Manica   Manica Bandula               God          6        no NULL
    ## 19    Manica   Manica Bandula               God         20       yes NULL
    ## 20    Manica   Manica Bandula               God         24       yes NULL
    ## 21    Manica   Manica Bandula               God         20       yes NULL
    ## 22    Manica   Manica Bandula               God         14        no NULL
    ## 23    Manica   Manica Bandula             Ruaca         12       yes NULL
    ## 24    Manica   Manica Bandula             Ruaca          8        no NULL
    ## 25    Manica   Manica Bandula             Ruaca         10       yes NULL
    ## 26    Manica   Manica Bandula             Ruaca          2       yes NULL
    ## 27    Manica   Manica Bandula             Ruaca         36        no NULL
    ## 28    Manica   Manica Bandula             Ruaca          2        no NULL
    ## 29    Manica   Manica Bandula             Ruaca         10       yes NULL
    ## 30    Manica   Manica Bandula             Ruaca         22       yes NULL
    ## 31    Manica   Manica Bandula             Ruaca         15       yes NULL
    ## 32    Manica   Manica Bandula             Ruaca         53       yes NULL
    ## 33    Manica   Manica Bandula             Ruaca         20       yes NULL
    ## 34    Manica   Manica Bandula          Chirodzo         18       yes NULL
    ## 35    Manica   Manica Bandula          Chirodzo         45       yes NULL
    ## 36    Manica   Manica Bandula          Chirodzo         23       yes NULL
    ## 37    Manica   Manica Bandula          Chirodzo          8        no NULL
    ## 38    Manica   Manica Bandula               God         19       yes NULL
    ## 39    Manica   Manica Bandula               God         22       yes NULL
    ## 40    Manica   Manica Bandula               God         23       yes NULL
    ## 41    Manica   Manica Bandula               God         22       yes NULL
    ## 42    Manica   Manica Bandula               God          8       yes NULL
    ## 43    Manica   Manica Bandula          Chirodzo          3        no NULL
    ## 44    Manica   Manica Bandula          Chirodzo          3        no NULL
    ## 45    Manica   Manica Bandula          Chirodzo         25       yes NULL
    ## 46    Manica   Manica Bandula          Chirodzo         21       yes NULL
    ## 47    Manica   Manica Bandula          Chirodzo          2       yes NULL
    ## 48    Manica   Manica Bandula          Chirodzo         48       yes NULL
    ## 49    Manica   Manica Bandula                49         12        no NULL
    ## 50    Manica   Manica Bandula          Chirodzo          6       yes NULL
    ## 51    Manica   Manica Bandula          Chirodzo         11       yes NULL
    ## 52    Manica   Manica Bandula          Chirodzo         15       yes NULL
    ## 53    Manica   Manica Bandula          Chirodzo         16       yes NULL
    ## 54    Manica   Manica Bandula          Chirodzo         10        no NULL
    ## 55    Manica   Manica Bandula          Chirodzo         23       yes NULL
    ## 56    Manica   Manica Bandula          Chirodzo         23       yes NULL
    ## 57    Manica   Manica Bandula          Chirodzo         20       yes NULL
    ## 58    Manica   Manica Bandula          Chirodzo         35       yes NULL
    ## 59    Manica   Manica Bandula          Chirodzo         60        no NULL
    ## 60    Manica  Bandula Bandula          Chirodzo         12       yes NULL
    ## 61    Manica   Manica Bandula          Chirodzo         14       yes NULL
    ## 62    Manica   Manica Bandula          Chirodzo          5        no NULL
    ## 63    Manica   Manica Bandula          Chirodzo          1       yes NULL
    ## 64    Manica   Manica Bandula          Chirodzo          1        no NULL
    ## 65    Manica   Manica Bandula          Chirodzo         20        no NULL
    ## 66    Manica   Manica Bandula          Chirodzo         16       yes NULL
    ## 67    Manica   Manica Bandula          Chirodzo          9       yes NULL
    ## 68    Manica   Manica Bandula          Chirodzo         21       yes NULL
    ## 69    Manica   Manica Bandula          Chirodzo         12       yes NULL
    ## 70    Manica   Manica Bandula          Chirodzo         20       yes NULL
    ## 71    Manica   Manica Bandula             Ruaca         12       yes NULL
    ## 72    Manica   Manica Bandula          Chirodzo         10       yes NULL
    ## 73    Manica   Manica Bandula             Ruaca          2        no NULL
    ## 74    Manica   Manica Bandula             Ruaca         15       yes NULL
    ## 75    Manica   Manica Bandula             Ruaca         41        no NULL
    ## 76    Manica   Manica Bandula               God          5        no NULL
    ## 77    Manica   Manica Bandula             Ruaca         20       yes NULL
    ## 78    Manica   Manica Bandula               God         11       yes NULL
    ## 79    Manica   Manica Bandula             Ruaca          4        no NULL
    ## 80    Manica   Manica Bandula               God         20       yes NULL
    ## 81    Manica   Manica Bandula               God         20        no NULL
    ## 82    Manica   Manica  Manica               God         24        no NULL
    ## 83    Manica   Manica Bandula               God          1       yes NULL
    ## 84    Manica   Manica Bandula               God          7       yes NULL
    ## 85    Manica   Manica Bandula               God         21       yes NULL
    ## 86    Manica   Manica Bandula               God         11        no NULL
    ## 87    Manica   Manica Bandula               God         11        no NULL
    ## 88    Manica   Manica Bandula               God          6       yes NULL
    ## 89    Manica   Manica Bandula               God         12       yes NULL
    ## 90    Manica   Manica Bandula             Ruaca         24       yes NULL
    ## 91    Manica   Manica Bandula             Ruaca          6       yes NULL
    ## 92    Manica   Manica Bandula             Ruaca         22       yes NULL
    ## 93    Manica   Manica Bandula             Ruaca         17       yes NULL
    ## 94    Manica   Manica Bandula             Ruaca         12       yes NULL
    ## 95    Manica   Manica Bandula               God         10        no NULL
    ## 96    Manica   Manica Bandula               God         10        no NULL
    ## 97    Manica   Manica Bandula             Ruaca         50        no NULL
    ## 98    Manica   Manica Bandula             Ruaca         15       yes NULL
    ## 99    Manica   Manica Bandula             Ruaca         20        no NULL
    ## 100   Manica   Manica Bandula             Ruaca         12        no NULL
    ## 101   Manica   Manica Bandula             Ruaca         35        no NULL
    ## 102   Manica   Manica Bandula             Ruaca         20       yes NULL
    ## 103   Manica   Manica Bandula               God         22       yes NULL
    ## 104   Manica   Manica Bandula               God         12       yes NULL
    ## 105   Manica   Manica Bandula             Ruaca         22        no NULL
    ## 106   Manica   Manica Bandula             Ruaca         16        no NULL
    ## 107   Manica   Manica Bandula             Ruaca          6        no NULL
    ## 108   Manica   Manica Bandula             Ruaca          7       yes NULL
    ## 109   Manica   Manica Bandula   Ruaca-Nhamuenda         14        no NULL
    ## 110   Manica   Manica Bandula Ruaca - Nhamuenda         16        no NULL
    ## 111   Manica   Manica Bandula               God         22        no NULL
    ## 112   Manica   Manica Bandula   Ruaca-Nhamuenda         21       yes NULL
    ## 113   Manica   Manica Bandula   Ruaca-Nhamuenda          1        no NULL
    ## 114   Manica   Manica Bandula             Ruaca          5        no NULL
    ## 115   Manica   Manica Bandula             Ruaca         24       yes NULL
    ## 116   Manica   Manica Bandula             Ruaca          8        no NULL
    ## 117   Manica   Manica Bandula               God         17       yes NULL
    ## 118   Manica   Manica Bandula               God          3       yes NULL
    ## 119   Manica   Manica Bandula             Ruaca         14        no NULL
    ## 120   Manica   Manica Bandula             Ruaca         16        no NULL
    ## 121   Manica   Manica Bandula             Ruaca         16        no NULL
    ## 122   Manica   Manica Bandula             Ruaca         13        no NULL
    ## 123   Manica   Manica Bandula             Ruaca         11        no NULL
    ## 124   Manica   Manica Bandula             Ruaca         10       yes NULL
    ## 125   Manica   Manica Bandula             Ruaca          3        no NULL
    ## 126   Manica   Manica Bandula          Chirodzo         15       yes NULL
    ## 127   Manica   Manica Bandula             Ruaca          5       yes NULL
    ## 128   Manica   Manica Bandula             Ruaca         10        no NULL
    ## 129   Manica   Manica Bandula             Ruaca          5        no NULL
    ## 130   Manica   Manica Bandula          Chirodzo         17       yes NULL
    ## 131   Manica   Manica Bandula          Chirodzo         20       yes NULL
    ##     X_membrs mbers_count remittance_money years_liv parents_liv sp_parents_liv
    ## 1          3           3               no         4          no            yes
    ## 2          7           7               no         9         yes            yes
    ## 3         10          10               no        15          no             no
    ## 4          7           7               no         6          no             no
    ## 5          7           7               no        40         yes             no
    ## 6          3           3               no         3          no             no
    ## 7          6           6               no        38         yes             no
    ## 8         12          12               no        70         yes            yes
    ## 9          8           8               no         6         yes             no
    ## 10        12          12               no        23          no             no
    ## 11         6           6               no        20         yes            yes
    ## 12         7           7              yes        20          no             no
    ## 13         6           6               no         8         yes             no
    ## 14        10          10               no        20         yes            yes
    ## 15         5           5               no        30         yes            yes
    ## 16         6           6               no        47         yes            yes
    ## 17         8           8               no        20          no             no
    ## 18         4           4               no        20         yes            yes
    ## 19         9           9               no        23         yes            yes
    ## 20         6           6               no         1         yes            yes
    ## 21         8           8               no        20          no            yes
    ## 22         4           4               no        20         yes            yes
    ## 23        10          10               no        20          no             no
    ## 24         6           6               no         4          no             no
    ## 25        11          11               no         6          no             no
    ## 26         3           3               no        20         yes            yes
    ## 27         7           7               no        36          no             no
    ## 28         2           2               no         2          no             no
    ## 29         7           7               no        10         yes             no
    ## 30         7           7              yes        22          no             no
    ## 31         3           3               no         2         yes            yes
    ## 32        19          19              yes        69         yes            yes
    ## 33         8           8               no        34         yes            yes
    ## 34         8           8               no        18          no             no
    ## 35         5           5               no        45          no             no
    ## 36         6           6               no        23          no             no
    ## 37         3           3               no         8         yes            yes
    ## 38        10          10              yes        19          no             no
    ## 39         6           6               no        22         yes            yes
    ## 40         9           9              yes        23          no            yes
    ## 41         7           7               no        22         yes            yes
    ## 42         8           8               no         8          no             no
    ## 43         7           7               no        29          no             no
    ## 44         2           2               no         6          no             no
    ## 45         9           9               no         7          no             no
    ## 46        10          10               no        42         yes            yes
    ## 47         2           2               no         2         yes            yes
    ## 48         7           7               no        58         yes             no
    ## 49         6           6               no        26         yes            yes
    ## 50         6           6               no         7          no             no
    ## 51         5           5               no        30         yes             no
    ## 52        11          11               no        15          no             no
    ## 53         8           8              yes        16         yes            yes
    ## 54         7           7              yes        15         yes             no
    ## 55         9           9               no        23         yes             no
    ## 56        12          12               no        23         yes            yes
    ## 57         4           4               no        27         yes            yes
    ## 58        11          11               no        45         yes            yes
    ## 59         2           2               no        60         yes            yes
    ## 60         8           8               no        15         yes            yes
    ## 61        10          10               no        14          no            yes
    ## 62         5           5               no         5         yes             no
    ## 63         4           4               no        10         yes            yes
    ## 64         6           6               no         1          no             no
    ## 65         8           8               no        20          no             no
    ## 66        10          10               no        37         yes             no
    ## 67         5           5               no        31         yes             no
    ## 68         8           8               no        52         yes            yes
    ## 69         4           4               no        12          no             no
    ## 70         8           8               no        25          no            yes
    ## 71         6           6               no        14         yes            yes
    ## 72         4           4               no        18          no             no
    ## 73         5           5              yes        25          no             no
    ## 74        10          10               no        16         yes             no
    ## 75         5           5               no        41         yes            yes
    ## 76         4           4               no         4          no             no
    ## 77         5           5               no        79         yes            yes
    ## 78        10          10               no        13          no             no
    ## 79         7           7               no        50         yes            yes
    ## 80        11          11               no        25         yes             no
    ## 81         7           7               no        21          no             no
    ## 82         7           7               no        24         yes             no
    ## 83         5           5               no        43         yes             no
    ## 84         5           5               no        48         yes            yes
    ## 85         7           7               no        49         yes            yes
    ## 86         5           5              yes        19         yes            yes
    ## 87         3           3               no        49          no             no
    ## 88         4           4               no         6         yes            yes
    ## 89        12          12               no        12          no             no
    ## 90         6           6               no        24         yes            yes
    ## 91         7           7               no         9         yes             no
    ## 92        17          17               no        48         yes            yes
    ## 93         5           5               no        22          no             no
    ## 94         7           7               no        40         yes            yes
    ## 95         5           5               no        10         yes            yes
    ## 96         3           3               no         4         yes            yes
    ## 97         6           6               no        96         yes            yes
    ## 98        12          12               no        15          no             no
    ## 99         6           6               no        48         yes             no
    ## 100        5           5               no        12          no             no
    ## 101       14          14               no        52         yes             no
    ## 102        6           6               no        40         yes             no
    ## 103       15          15               no        22          no             no
    ## 104        4           4               no        12         yes             no
    ## 105        6           6               no        22         yes            yes
    ## 106       11          11              yes        26         yes             no
    ## 107        5           5               no        25         yes            yes
    ## 108        5           5               no        14          no            yes
    ## 109        3           3              yes        14         yes             no
    ## 110        4           4               no        16         yes            yes
    ## 111       15          15               no        22          no            yes
    ## 112        5           5               no        25          no             no
    ## 113       10          10               no        28         yes            yes
    ## 114        7           7               no         5         yes            yes
    ## 115       10          10               no        24         yes             no
    ## 116        7           7               no         8          no            yes
    ## 117        4           4               no        24         yes             no
    ## 118        7           7               no        13         yes            yes
    ## 119        9           9               no        14          no             no
    ## 120       11          11               no        16         yes            yes
    ## 121        8           8               no        24         yes             no
    ## 122       12          12               no        25         yes            yes
    ## 123        7           7               no        36         yes            yes
    ## 124       15          15               no        16          no            yes
    ## 125       10          10               no         5         yes             no
    ## 126        9           9               no        20         yes            yes
    ## 127        3           3               no         7         yes            yes
    ## 128        7           7               no        10          no             no
    ## 129        4           4               no         5          no             no
    ## 130        7           7               no        17          no             no
    ## 131        8           8               no        20          no            yes
    ##     grand_liv sp_grand_liv respondent_roof_type respondent_wall_type
    ## 1          no          yes                grass              muddaub
    ## 2         yes          yes                grass              muddaub
    ## 3          no           no        mabatisloping          burntbricks
    ## 4          no           no        mabatisloping          burntbricks
    ## 5         yes           no                grass          burntbricks
    ## 6          no           no                grass              muddaub
    ## 7         yes           no                grass              muddaub
    ## 8         yes          yes        mabatisloping          burntbricks
    ## 9         yes           no                grass          burntbricks
    ## 10         no           no        mabatisloping          burntbricks
    ## 11         no          yes                grass            sunbricks
    ## 12         no           no        mabatisloping          burntbricks
    ## 13        yes           no                grass          burntbricks
    ## 14         no          yes                grass          burntbricks
    ## 15        yes          yes                grass            sunbricks
    ## 16        yes          yes                grass              muddaub
    ## 17         no           no                grass            sunbricks
    ## 18         no          yes                grass              muddaub
    ## 19        yes          yes        mabatisloping          burntbricks
    ## 20        yes          yes                grass          burntbricks
    ## 21         no          yes        mabatisloping          burntbricks
    ## 22        yes          yes                grass              muddaub
    ## 23         no           no        mabatisloping          burntbricks
    ## 24         no           no        mabatisloping          burntbricks
    ## 25         no           no        mabatisloping          burntbricks
    ## 26        yes          yes        mabatisloping          burntbricks
    ## 27         no           no                grass          burntbricks
    ## 28         no           no                grass              muddaub
    ## 29        yes           no        mabatisloping          burntbricks
    ## 30         no           no                grass              muddaub
    ## 31        yes          yes                grass              muddaub
    ## 32        yes           no        mabatipitched              muddaub
    ## 33        yes          yes                grass              muddaub
    ## 34         no           no        mabatisloping          burntbricks
    ## 35         no           no                grass              muddaub
    ## 36         no           no        mabatisloping            sunbricks
    ## 37         no           no        mabatisloping          burntbricks
    ## 38         no           no                grass              muddaub
    ## 39        yes          yes        mabatisloping              muddaub
    ## 40        yes          yes                grass          burntbricks
    ## 41        yes          yes                grass              muddaub
    ## 42         no           no                grass            sunbricks
    ## 43         no           no                grass              muddaub
    ## 44         no           no                grass              muddaub
    ## 45         no           no                grass              muddaub
    ## 46        yes          yes        mabatisloping          burntbricks
    ## 47        yes          yes                grass              muddaub
    ## 48        yes           no                grass              muddaub
    ## 49        yes          yes        mabatisloping          burntbricks
    ## 50         no           no                grass              muddaub
    ## 51        yes           no                grass              muddaub
    ## 52         no           no        mabatisloping          burntbricks
    ## 53        yes          yes        mabatisloping          burntbricks
    ## 54        yes           no                grass              muddaub
    ## 55        yes           no                grass              muddaub
    ## 56        yes          yes        mabatisloping          burntbricks
    ## 57        yes          yes                grass          burntbricks
    ## 58        yes          yes        mabatisloping          burntbricks
    ## 59        yes          yes                grass              muddaub
    ## 60        yes          yes                grass          burntbricks
    ## 61        yes          yes                grass              muddaub
    ## 62         no           no                grass              muddaub
    ## 63         no          yes                grass              muddaub
    ## 64         no           no                grass              muddaub
    ## 65         no           no        mabatisloping          burntbricks
    ## 66         no           no        mabatipitched          burntbricks
    ## 67        yes           no        mabatipitched          burntbricks
    ## 68         no           no        mabatipitched          burntbricks
    ## 69         no           no                grass              muddaub
    ## 70         no           no        mabatipitched          burntbricks
    ## 71        yes          yes                grass          burntbricks
    ## 72         no           no                grass          burntbricks
    ## 73         no           no        mabatisloping          burntbricks
    ## 74        yes           no                grass          burntbricks
    ## 75        yes          yes                grass          burntbricks
    ## 76         no           no                grass          burntbricks
    ## 77        yes           no        mabatisloping          burntbricks
    ## 78         no           no                grass            sunbricks
    ## 79        yes          yes                grass              muddaub
    ## 80        yes           no        mabatipitched            sunbricks
    ## 81         no           no        mabatipitched              muddaub
    ## 82        yes           no                grass              muddaub
    ## 83         no          yes                grass              muddaub
    ## 84         no           no                grass          burntbricks
    ## 85        yes          yes        mabatisloping          burntbricks
    ## 86         no           no        mabatisloping          burntbricks
    ## 87         no           no                grass          burntbricks
    ## 88        yes          yes                grass              muddaub
    ## 89         no           no        mabatisloping          burntbricks
    ## 90        yes          yes                grass              muddaub
    ## 91         no           no        mabatisloping          burntbricks
    ## 92        yes          yes        mabatipitched          burntbricks
    ## 93         no           no        mabatisloping          burntbricks
    ## 94        yes          yes                grass            sunbricks
    ## 95         no          yes        mabatisloping          burntbricks
    ## 96         no           no                grass              muddaub
    ## 97        yes          yes        mabatisloping            sunbricks
    ## 98         no           no        mabatisloping          burntbricks
    ## 99        yes           no        mabatipitched          burntbricks
    ## 100        no           no        mabatipitched              muddaub
    ## 101       yes           no                grass            sunbricks
    ## 102       yes           no        mabatisloping            sunbricks
    ## 103        no           no        mabatisloping            sunbricks
    ## 104       yes           no                grass            sunbricks
    ## 105       yes          yes        mabatisloping            sunbricks
    ## 106        no           no        mabatisloping          burntbricks
    ## 107       yes           no                grass              muddaub
    ## 108        no          yes        mabatisloping          burntbricks
    ## 109        no           no                grass              muddaub
    ## 110        no           no        mabatisloping            sunbricks
    ## 111        no          yes        mabatisloping          burntbricks
    ## 112        no           no                grass          burntbricks
    ## 113       yes           no                grass              muddaub
    ## 114       yes          yes        mabatisloping          burntbricks
    ## 115        no           no                grass          burntbricks
    ## 116        no          yes                grass              muddaub
    ## 117       yes           no                grass            sunbricks
    ## 118       yes          yes        mabatisloping          burntbricks
    ## 119        no           no                grass          burntbricks
    ## 120       yes          yes                grass              muddaub
    ## 121       yes           no                grass              muddaub
    ## 122       yes          yes                grass          burntbricks
    ## 123       yes          yes        mabatisloping          burntbricks
    ## 124        no          yes        mabatisloping            sunbricks
    ## 125       yes           no        mabatisloping          burntbricks
    ## 126       yes          yes                grass          burntbricks
    ## 127       yes          yes                grass          burntbricks
    ## 128        no           no        mabatisloping               cement
    ## 129       yes           no                grass              muddaub
    ## 130        no           no        mabatisloping          burntbricks
    ## 131        no          yes        mabatisloping          burntbricks
    ##     respondent_wall_type_other respondent_floor_type window_type
    ## 1                         NULL                 earth          no
    ## 2                         NULL                 earth          no
    ## 3                         NULL                cement         yes
    ## 4                         NULL                 earth          no
    ## 5                         NULL                 earth          no
    ## 6                         NULL                 earth          no
    ## 7                         NULL                 earth          no
    ## 8                         NULL                cement          no
    ## 9                         NULL                 earth          no
    ## 10                        NULL                cement         yes
    ## 11                        NULL                 earth          no
    ## 12                        NULL                cement          no
    ## 13                        NULL                 earth          no
    ## 14                        NULL                 earth          no
    ## 15                        NULL                 earth          no
    ## 16                        NULL                 earth         yes
    ## 17                        NULL                 earth          no
    ## 18                        NULL                 earth          no
    ## 19                        NULL                 earth          no
    ## 20                        NULL                 earth         yes
    ## 21                        NULL                cement          no
    ## 22                        NULL                 earth          no
    ## 23                        NULL                cement         yes
    ## 24                        NULL                cement         yes
    ## 25                        NULL                cement          no
    ## 26                        NULL                 earth          no
    ## 27                        NULL                 earth          no
    ## 28                        NULL                 earth          no
    ## 29                        NULL                 earth          no
    ## 30                        NULL                 earth          no
    ## 31                        NULL                 earth          no
    ## 32                        NULL                 earth          no
    ## 33                        NULL                cement          no
    ## 34                        NULL                cement         yes
    ## 35                        NULL                 earth          no
    ## 36                        NULL                 earth          no
    ## 37                        NULL                 earth          no
    ## 38                        NULL                 earth          no
    ## 39                        NULL                 earth          no
    ## 40                        NULL                 earth          no
    ## 41                        NULL                 earth          no
    ## 42                        NULL                 earth         yes
    ## 43                        NULL                 earth          no
    ## 44                        NULL                 earth          no
    ## 45                        NULL                 earth          no
    ## 46                        NULL                cement          no
    ## 47                        NULL                 earth          no
    ## 48                        NULL                 earth          no
    ## 49                        NULL                 earth         yes
    ## 50                        NULL                 earth          no
    ## 51                        NULL                cement          no
    ## 52                        NULL                cement         yes
    ## 53                        NULL                cement          no
    ## 54                        NULL                 earth          no
    ## 55                        NULL                 earth          no
    ## 56                        NULL                cement          no
    ## 57                        NULL                 earth          no
    ## 58                        NULL                 earth          no
    ## 59                        NULL                 earth          no
    ## 60                        NULL                 earth          no
    ## 61                        NULL                 earth          no
    ## 62                        NULL                 earth          no
    ## 63                        NULL                 earth          no
    ## 64                        NULL                 earth          no
    ## 65                        NULL                 earth          no
    ## 66                        NULL                cement         yes
    ## 67                        NULL                cement         yes
    ## 68                        NULL                 earth          no
    ## 69                        NULL                 earth          no
    ## 70                        NULL                 earth          no
    ## 71                        NULL                 earth          no
    ## 72                        NULL                 earth          no
    ## 73                        NULL                 earth          no
    ## 74                        NULL                cement          no
    ## 75                        NULL                 earth          no
    ## 76                        NULL                 earth          no
    ## 77                        NULL                 earth          no
    ## 78                        NULL                 earth          no
    ## 79                        NULL                 earth          no
    ## 80                        NULL                 earth         yes
    ## 81                        NULL                 earth          no
    ## 82                        NULL                 earth          no
    ## 83                        NULL                 earth          no
    ## 84                        NULL                 earth          no
    ## 85                        NULL                 earth          no
    ## 86                        NULL                cement         yes
    ## 87                        NULL                 earth          no
    ## 88                        NULL                 earth          no
    ## 89                        NULL                cement          no
    ## 90                        NULL                 earth          no
    ## 91                        NULL                cement          no
    ## 92                        NULL                cement          no
    ## 93                        NULL                 earth          no
    ## 94                        NULL                 earth          no
    ## 95                        NULL                cement         yes
    ## 96                        NULL                 earth          no
    ## 97                        NULL                 earth          no
    ## 98                        NULL                 earth          no
    ## 99                        NULL                 earth          no
    ## 100                       NULL                 earth          no
    ## 101                       NULL                cement          no
    ## 102                       NULL                 earth          no
    ## 103                       NULL                cement         yes
    ## 104                       NULL                 earth          no
    ## 105                       NULL                cement          no
    ## 106                       NULL                cement          no
    ## 107                       NULL                 earth          no
    ## 108                       NULL                 earth          no
    ## 109                       NULL                 earth          no
    ## 110                       NULL                cement          no
    ## 111                       NULL                cement          no
    ## 112                       NULL                cement          no
    ## 113                       NULL                cement          no
    ## 114                       NULL                cement          no
    ## 115                       NULL                 earth          no
    ## 116                       NULL                 earth          no
    ## 117                       NULL                 earth          no
    ## 118                       NULL                 earth          no
    ## 119                       NULL                 earth          no
    ## 120                       NULL                 earth          no
    ## 121                       NULL                 earth          no
    ## 122                       NULL                cement          no
    ## 123                       NULL                 earth          no
    ## 124                       NULL                 earth          no
    ## 125                       NULL                cement         yes
    ## 126                       NULL                cement         yes
    ## 127                       NULL                 earth          no
    ## 128                       NULL                cement         yes
    ## 129                       NULL                 earth          no
    ## 130                       NULL                cement         yes
    ## 131                       NULL                cement          no
    ##     buildings_in_compound rooms other_buildings X_plots ots_count water_use
    ## 1                       1     1              no       2         2        no
    ## 2                       1     1              no       3         3       yes
    ## 3                       1     1              no       1         1        no
    ## 4                       1     1              no       3         3        no
    ## 5                       1     1              no       2         2        no
    ## 6                       1     1              no       1         1        no
    ## 7                       1     1             yes       4         4       yes
    ## 8                       2     3             yes       2         2       yes
    ## 9                       2     1             yes       3         3       yes
    ## 10                      1     5              no       2         2       yes
    ## 11                      2     1              no       2         2        no
    ## 12                      2     3              no       2         2       yes
    ## 13                      1     1              no       4         4       yes
    ## 14                      3     3              no       3         3        no
    ## 15                      1     2             yes       3         3       yes
    ## 16                      2     1             yes       1         1        no
    ## 17                      2     1              no       3         3        no
    ## 18                      1     1              no       2         2        no
    ## 19                      1     2             yes       2         2        no
    ## 20                      1     1              no       2         2        no
    ## 21                      1     1              no       4         4       yes
    ## 22                      1     1              no       1         1        no
    ## 23                      1     4             yes       2         2        no
    ## 24                      2     2             yes       3         3       yes
    ## 25                      2     3             yes       3         3       yes
    ## 26                      2     2              no       2         2       yes
    ## 27                      3     2             yes       2         2        no
    ## 28                      1     1             yes       3         3       yes
    ## 29                      1     2             yes       3         3       yes
    ## 30                      1     2              no       1         1        no
    ## 31                      7     1              no       1         1        no
    ## 32                      8     2             yes       8         8       yes
    ## 33                      2     1              no       2         2       yes
    ## 34                      2     3             yes       2         2       yes
    ## 35                      3     1              no       2         2       yes
    ## 36                      1     1              no       3         3       yes
    ## 37                      3     1              no       1         1        no
    ## 38                      3     1              no       2         2       yes
    ## 39                      1     1              no       1         1        no
    ## 40                      1     1              no       2         2       yes
    ## 41                      1     1              no       1         1        no
    ## 42                      1     1              no       2         2       yes
    ## 43                      2     1              no       4         4       yes
    ## 44                      2     1              no       1         1        no
    ## 45                      2     1              no       3         3       yes
    ## 46                      3     2              no       5         5       yes
    ## 47                      1     1             yes       2         2       yes
    ## 48                      1     1              no       1         1        no
    ## 49                      2     2              no       1         1        no
    ## 50                      1     1              no       1         1       yes
    ## 51                      1     1              no       1         1        no
    ## 52                      1     3             yes       1         1       yes
    ## 53                      2     3              no       3         3       yes
    ## 54                      3     1              no       1         1       yes
    ## 55                      2     2              no       1         1        no
    ## 56                      4     2              no       2         2       yes
    ## 57                      4     1              no       2         2       yes
    ## 58                      5     3              no       3         3       yes
    ## 59                      1     3             yes       2         2        no
    ## 60                      3     2              no       3         3       yes
    ## 61                      4     1              no       2         2       yes
    ## 62                      3     1              no       2         2        no
    ## 63                      1     1             yes       1         1        no
    ## 64                      2     1              no       2         2        no
    ## 65                      2     3              no       2         2       yes
    ## 66                      5     3             yes       1         1       yes
    ## 67                      1     2              no       1         1       yes
    ## 68                      3     3              no       3         3       yes
    ## 69                      2     1              no       1         1       yes
    ## 70                      2     2             yes       3         3       yes
    ## 71                      1     1              no       2         2       yes
    ## 72                      3     8              no       1         1        no
    ## 73                      1     2             yes       1         1       yes
    ## 74                      3     1              no       2         2       yes
    ## 75                      1     1              no       1         1        no
    ## 76                      2     1              no       2         2        no
    ## 77                      1     2             yes       3         3       yes
    ## 78                      2     1              no       2         2       yes
    ## 79                      1     1             yes       2         2       yes
    ## 80                      4     2             yes       1         1       yes
    ## 81                      2     3             yes       1         1       yes
    ## 82                      1     1              no       1         1       yes
    ## 83                      3     2             yes       2         2       yes
    ## 84                      3     1              no       3         3       yes
    ## 85                      2     2              no       2         2       yes
    ## 86                      1     2              no       2         2       yes
    ## 87                      1     1              no       2         2       yes
    ## 88                      1     2              no       2         2        no
    ## 89                      2     4             yes       2         2       yes
    ## 90                      2     1              no       3         3       yes
    ## 91                      2     2              no       3         3       yes
    ## 92                      5     2              no       6         6       yes
    ## 93                      2     1              no       2         2       yes
    ## 94                      3     1              no       3         3       yes
    ## 95                      2     2             yes       2         2       yes
    ## 96                      1     1              no       2         2       yes
    ## 97                      2     1              no       2         2       yes
    ## 98                      3     2              no       2         2       yes
    ## 99                      2     1              no       2         2       yes
    ## 100                     1     1              no       1         1       yes
    ## 101                     4     1             yes       4         4       yes
    ## 102                     2     1              no       2         2       yes
    ## 103                     4     5             yes       5         5       yes
    ## 104                     1     1             yes       3         3        no
    ## 105                     2     3             yes       3         3       yes
    ## 106                     2     3             yes       3         3       yes
    ## 107                     2     1              no       1         1        no
    ## 108                     1     1              no       3         3       yes
    ## 109                     4     1              no       2         2       yes
    ## 110                     3     2             yes       2         2        no
    ## 111                     3     2             yes       3         3       yes
    ## 112                     2     3             yes       1         1        no
    ## 113                     1     4              no       1         1        no
    ## 114                     3     4              no       2         2       yes
    ## 115                     3     2             yes       3         3       yes
    ## 116                     2     1              no       2         2       yes
    ## 117                     2     1              no       2         2       yes
    ## 118                     2     2              no       3         3       yes
    ## 119                     1     1             yes       2         2       yes
    ## 120                     2     1              no       3         3       yes
    ## 121                     5     1              no       2         2       yes
    ## 122                     2     2             yes       3         3       yes
    ## 123                     2     1              no       2         2       yes
    ## 124                     2     1             yes       3         3       yes
    ## 125                     1     4             yes       2         2       yes
    ## 126                     4     1              no       3         3       yes
    ## 127                     1     1              no       2         2       yes
    ## 128                     3     3             yes       4         4       yes
    ## 129                     2     1              no       2         2       yes
    ## 130                     1     2              no       2         2       yes
    ## 131                     1     2             yes       2         2        no
    ##     X_group_count s_group_count no_enough_water
    ## 1               2          NULL            NULL
    ## 2            NULL             3             yes
    ## 3               1          NULL            NULL
    ## 4               3          NULL            NULL
    ## 5               2          NULL            NULL
    ## 6               1          NULL            NULL
    ## 7            NULL             4             yes
    ## 8            NULL             2             yes
    ## 9            NULL             3             yes
    ## 10           NULL             2             yes
    ## 11              2          NULL            NULL
    ## 12           NULL             2             yes
    ## 13           NULL             4             yes
    ## 14              3          NULL            NULL
    ## 15           NULL             3             yes
    ## 16              1          NULL            NULL
    ## 17              3          NULL            NULL
    ## 18              2          NULL            NULL
    ## 19              2          NULL            NULL
    ## 20              2          NULL            NULL
    ## 21           NULL             4             yes
    ## 22              1          NULL            NULL
    ## 23              2          NULL            NULL
    ## 24           NULL             3             yes
    ## 25           NULL             3             yes
    ## 26           NULL             2             yes
    ## 27              2          NULL            NULL
    ## 28           NULL             3             yes
    ## 29           NULL             3             yes
    ## 30              1          NULL            NULL
    ## 31              1          NULL            NULL
    ## 32           NULL             8             yes
    ## 33           NULL             2             yes
    ## 34           NULL             2             yes
    ## 35           NULL             2             yes
    ## 36           NULL             3              no
    ## 37              1          NULL            NULL
    ## 38           NULL             2             yes
    ## 39              1          NULL            NULL
    ## 40           NULL             2             yes
    ## 41              1          NULL            NULL
    ## 42           NULL             2             yes
    ## 43           NULL             4              no
    ## 44              1          NULL            NULL
    ## 45           NULL             3             yes
    ## 46           NULL             5             yes
    ## 47           NULL             2             yes
    ## 48              1          NULL            NULL
    ## 49              1          NULL            NULL
    ## 50           NULL             1             yes
    ## 51              1          NULL            NULL
    ## 52           NULL             1             yes
    ## 53           NULL             3             yes
    ## 54           NULL             1             yes
    ## 55              1          NULL            NULL
    ## 56           NULL             2             yes
    ## 57           NULL             2              no
    ## 58           NULL             3              no
    ## 59              2          NULL            NULL
    ## 60           NULL             3             yes
    ## 61           NULL             2             yes
    ## 62              2          NULL            NULL
    ## 63              1          NULL            NULL
    ## 64              2          NULL            NULL
    ## 65           NULL             2             yes
    ## 66           NULL             1             yes
    ## 67           NULL             1             yes
    ## 68           NULL             3             yes
    ## 69           NULL             1             yes
    ## 70           NULL             3             yes
    ## 71           NULL             2             yes
    ## 72              1          NULL            NULL
    ## 73           NULL             1             yes
    ## 74           NULL             2             yes
    ## 75              1          NULL            NULL
    ## 76              2          NULL            NULL
    ## 77           NULL             3             yes
    ## 78           NULL             2             yes
    ## 79           NULL             2             yes
    ## 80           NULL             1             yes
    ## 81           NULL             1             yes
    ## 82           NULL             1             yes
    ## 83           NULL             2             yes
    ## 84           NULL             3             yes
    ## 85           NULL             2             yes
    ## 86           NULL             2             yes
    ## 87           NULL             2             yes
    ## 88              2          NULL            NULL
    ## 89           NULL             2             yes
    ## 90           NULL             3             yes
    ## 91           NULL             3             yes
    ## 92           NULL             6             yes
    ## 93           NULL             2             yes
    ## 94           NULL             3             yes
    ## 95           NULL             2             yes
    ## 96           NULL             2             yes
    ## 97           NULL             2             yes
    ## 98           NULL             2             yes
    ## 99           NULL             2             yes
    ## 100          NULL             1             yes
    ## 101          NULL             4             yes
    ## 102          NULL             2             yes
    ## 103          NULL             5             yes
    ## 104             3          NULL            NULL
    ## 105          NULL             3             yes
    ## 106          NULL             3             yes
    ## 107             1          NULL            NULL
    ## 108          NULL             3             yes
    ## 109          NULL             2              no
    ## 110             2          NULL            NULL
    ## 111          NULL             3             yes
    ## 112             1          NULL            NULL
    ## 113             1          NULL            NULL
    ## 114          NULL             2             yes
    ## 115          NULL             3             yes
    ## 116          NULL             2             yes
    ## 117          NULL             2              no
    ## 118          NULL             3             yes
    ## 119          NULL             2             yes
    ## 120          NULL             3             yes
    ## 121          NULL             2             yes
    ## 122          NULL             3             yes
    ## 123          NULL             2             yes
    ## 124          NULL             3             yes
    ## 125          NULL             2             yes
    ## 126          NULL             3             yes
    ## 127          NULL             2             yes
    ## 128          NULL             4             yes
    ## 129          NULL             2             yes
    ## 130          NULL             2             yes
    ## 131             2          NULL            NULL
    ##                                                               months_no_water
    ## 1                                                                        NULL
    ## 2                                                           ['Aug' ;  'Sept']
    ## 3                                                                        NULL
    ## 4                                                                        NULL
    ## 5                                                                        NULL
    ## 6                                                                        NULL
    ## 7                                                  ['Aug' ;  'Sept' ;  'Oct']
    ## 8                                                           ['Sept' ;  'Oct']
    ## 9                                                            ['Oct' ;  'Nov']
    ## 10                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 11                                                                       NULL
    ## 12                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 13                                                                    ['Oct']
    ## 14                                                                       NULL
    ## 15                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 16                                                                       NULL
    ## 17                                                                       NULL
    ## 18                                                                       NULL
    ## 19                                                                       NULL
    ## 20                                                                       NULL
    ## 21                                                                    ['Oct']
    ## 22                                                                       NULL
    ## 23                                                                       NULL
    ## 24                                                          ['Sept' ;  'Oct']
    ## 25                                                          ['Aug' ;  'Sept']
    ## 26                                                           ['Oct' ;  'Nov']
    ## 27                                                                       NULL
    ## 28                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 29                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 30                                                                       NULL
    ## 31                                                                       NULL
    ## 32                                                          ['Sept' ;  'Oct']
    ## 33                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 34                                                           ['Oct' ;  'Nov']
    ## 35                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 36                                                                       NULL
    ## 37                                                                       NULL
    ## 38                                                          ['Sept' ;  'Oct']
    ## 39                                                                       NULL
    ## 40                                                          ['Sept' ;  'Oct']
    ## 41                                                                       NULL
    ## 42                                                          ['Aug' ;  'Sept']
    ## 43                                                                       NULL
    ## 44                                                                       NULL
    ## 45                                                          ['Sept' ;  'Oct']
    ## 46                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 47                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 48                                                                       NULL
    ## 49                                                                       NULL
    ## 50                                                          ['Sept' ;  'Oct']
    ## 51                                                                       NULL
    ## 52                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 53                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 54                               ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 55                                                                       NULL
    ## 56                                                          ['Sept' ;  'Oct']
    ## 57                                                                       NULL
    ## 58                                                                       NULL
    ## 59                                                                       NULL
    ## 60                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 61                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 62                                                                       NULL
    ## 63                                                                       NULL
    ## 64                                                                       NULL
    ## 65                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 66                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 67                                                           ['Oct' ;  'Nov']
    ## 68                                                           ['Nov' ;  'Dec']
    ## 69                                                           ['Nov' ;  'Dec']
    ## 70                                                          ['Aug' ;  'Sept']
    ## 71                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 72                                                                       NULL
    ## 73                                                                    ['Nov']
    ## 74                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 75                                                                       NULL
    ## 76                                                                       NULL
    ## 77                                                           ['Oct' ;  'Nov']
    ## 78                                                           ['Oct' ;  'Nov']
    ## 79                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 80                                                          ['Sept' ;  'Oct']
    ## 81                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 82                                                          ['Sept' ;  'Oct']
    ## 83                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 84                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 85                                                           ['Oct' ;  'Nov']
    ## 86                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 87                                                           ['Jan' ;  'Dec']
    ## 88                                                                       NULL
    ## 89                               ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 90                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 91                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 92                                                          ['Sept' ;  'Oct']
    ## 93                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 94                                                          ['Sept' ;  'Oct']
    ## 95                                                          ['Sept' ;  'Oct']
    ## 96                                                 ['Sept' ;  'Oct' ;  'Nov']
    ## 97                                        ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 98                                                 ['Aug' ;  'Sept' ;  'Oct']
    ## 99                                                          ['Aug' ;  'Sept']
    ## 100                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 101                                                         ['Aug' ;  'Sept']
    ## 102                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 103                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 104                                                                      NULL
    ## 105                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 106                                                         ['Sept' ;  'Oct']
    ## 107                                                                      NULL
    ## 108                                       ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 109                                                                      NULL
    ## 110                                                                      NULL
    ## 111                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 112                                                                      NULL
    ## 113                                                                      NULL
    ## 114                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 115                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 116 ['Apr' ;  'May' ;  'June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 117                                                                      NULL
    ## 118                                                          ['Jan' ;  'Dec']
    ## 119                              ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 120                                                ['Aug' ;  'Sept' ;  'Oct']
    ## 121                    ['July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 122                                       ['Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 123                                                          ['Oct' ;  'Nov']
    ## 124                              ['Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 125                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 126                                                         ['Sept' ;  'Nov']
    ## 127                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 128                                                 ['Oct' ;  'Nov' ;  'Dec']
    ## 129                                                ['Aug' ;  'Sept' ;  'Oct']
    ## 130                                                ['Sept' ;  'Oct' ;  'Nov']
    ## 131                                                                      NULL
    ##     period_use exper_other other_meth
    ## 1         NULL        NULL       NULL
    ## 2            2         yes         no
    ## 3         NULL        NULL       NULL
    ## 4         NULL        NULL       NULL
    ## 5         NULL        NULL       NULL
    ## 6         NULL        NULL       NULL
    ## 7           10         yes         no
    ## 8           10         yes         no
    ## 9            6         yes         no
    ## 10          22         yes         no
    ## 11        NULL        NULL       NULL
    ## 12          20         yes         no
    ## 13           7         yes         no
    ## 14        NULL        NULL       NULL
    ## 15          30         yes         no
    ## 16        NULL        NULL       NULL
    ## 17        NULL        NULL       NULL
    ## 18        NULL        NULL       NULL
    ## 19        NULL        NULL       NULL
    ## 20        NULL        NULL       NULL
    ## 21          20         yes         no
    ## 22        NULL        NULL       NULL
    ## 23        NULL        NULL       NULL
    ## 24           8         yes         no
    ## 25          10         yes         no
    ## 26           2         yes         no
    ## 27        NULL        NULL       NULL
    ## 28           2         yes         no
    ## 29           4         yes        yes
    ## 30        NULL        NULL       NULL
    ## 31        NULL        NULL       NULL
    ## 32          45         yes         no
    ## 33          20         yes         no
    ## 34           2         yes         no
    ## 35          20         yes         no
    ## 36          23         yes         no
    ## 37        NULL        NULL       NULL
    ## 38           9         yes         no
    ## 39        NULL        NULL       NULL
    ## 40          23         yes         no
    ## 41        NULL        NULL       NULL
    ## 42           5         yes         no
    ## 43           3         yes         no
    ## 44        NULL        NULL       NULL
    ## 45          20         yes         no
    ## 46          21         yes         no
    ## 47           2         yes         no
    ## 48        NULL        NULL       NULL
    ## 49        NULL        NULL       NULL
    ## 50           1          no         no
    ## 51        NULL        NULL       NULL
    ## 52          15          no         no
    ## 53          16         yes         no
    ## 54          10         yes         no
    ## 55        NULL        NULL       NULL
    ## 56          23         yes         no
    ## 57          20         yes         no
    ## 58          35         yes         no
    ## 59        NULL        NULL       NULL
    ## 60          12         yes         no
    ## 61          13         yes         no
    ## 62        NULL        NULL       NULL
    ## 63        NULL        NULL       NULL
    ## 64        NULL        NULL       NULL
    ## 65          20         yes         no
    ## 66          10          no         no
    ## 67           9         yes         no
    ## 68          21         yes         no
    ## 69          12         yes         no
    ## 70          20         yes         no
    ## 71           1         yes         no
    ## 72        NULL        NULL       NULL
    ## 73           2         yes         no
    ## 74          16         yes         no
    ## 75        NULL        NULL       NULL
    ## 76        NULL        NULL       NULL
    ## 77          20         yes         no
    ## 78          11          no         no
    ## 79           4         yes         no
    ## 80          23         yes         no
    ## 81          20         yes         no
    ## 82          21         yes         no
    ## 83          24         yes         no
    ## 84           5         yes         no
    ## 85          21         yes         no
    ## 86          11         yes         no
    ## 87          11         yes         no
    ## 88        NULL        NULL       NULL
    ## 89           9         yes         no
    ## 90           4         yes         no
    ## 91           4         yes        yes
    ## 92          22         yes         no
    ## 93          17         yes         no
    ## 94          12         yes         no
    ## 95          10          no         no
    ## 96          10         yes         no
    ## 97          10         yes         no
    ## 98           2         yes         no
    ## 99          20         yes         no
    ## 100         12         yes         no
    ## 101         16         yes         no
    ## 102          1         yes         no
    ## 103         21         yes         no
    ## 104       NULL        NULL       NULL
    ## 105         22         yes         no
    ## 106          2         yes         no
    ## 107       NULL        NULL       NULL
    ## 108          3         yes        yes
    ## 109          3         yes         no
    ## 110       NULL        NULL       NULL
    ## 111         16         yes         no
    ## 112       NULL        NULL       NULL
    ## 113       NULL        NULL       NULL
    ## 114          5         yes         no
    ## 115         12         yes         no
    ## 116          8         yes         no
    ## 117          2         yes         no
    ## 118          3         yes         no
    ## 119         10         yes         no
    ## 120          2         yes         no
    ## 121         16         yes         no
    ## 122         13         yes        yes
    ## 123         11         yes         no
    ## 124          7         yes         no
    ## 125          3         yes         no
    ## 126          5         yes         no
    ## 127          4         yes         no
    ## 128         10         yes         no
    ## 129          2         yes         no
    ## 130          6         yes         no
    ## 131       NULL        NULL       NULL
    ##                                            res_change memb_assoc resp_assoc
    ## 1                                                NULL       NULL       NULL
    ## 2                                                NULL        yes         no
    ## 3                                                NULL       NULL       NULL
    ## 4                                                NULL       NULL       NULL
    ## 5                                                NULL       NULL       NULL
    ## 6                                                NULL       NULL       NULL
    ## 7                                                NULL         no       NULL
    ## 8                                                NULL        yes        yes
    ## 9                                                NULL         no       NULL
    ## 10                                               NULL         no       NULL
    ## 11                                               NULL       NULL       NULL
    ## 12                                               NULL        yes         no
    ## 13                                               NULL         no       NULL
    ## 14                                               NULL       NULL       NULL
    ## 15                                               NULL        yes         no
    ## 16                                               NULL       NULL       NULL
    ## 17                                               NULL       NULL       NULL
    ## 18                                               NULL       NULL       NULL
    ## 19                                               NULL       NULL       NULL
    ## 20                                               NULL       NULL       NULL
    ## 21                                               NULL         no       NULL
    ## 22                                               NULL       NULL       NULL
    ## 23                                               NULL       NULL       NULL
    ## 24                                               NULL         no       NULL
    ## 25                                               NULL         no       NULL
    ## 26                                               NULL         no       NULL
    ## 27                                               NULL       NULL       NULL
    ## 28                                               NULL         no       NULL
    ## 29                                      ['less_work']        yes        yes
    ## 30                                               NULL       NULL       NULL
    ## 31                                               NULL       NULL       NULL
    ## 32                                               NULL        yes         no
    ## 33                                               NULL         no       NULL
    ## 34                                               NULL        yes         no
    ## 35                                               NULL        yes         no
    ## 36                                               NULL        yes         no
    ## 37                                               NULL       NULL       NULL
    ## 38                                               NULL        yes         no
    ## 39                                               NULL       NULL       NULL
    ## 40                                               NULL        yes         no
    ## 41                                               NULL       NULL       NULL
    ## 42                                               NULL         no       NULL
    ## 43                                               NULL         no       NULL
    ## 44                                               NULL       NULL       NULL
    ## 45                                               NULL         no       NULL
    ## 46                                               NULL         no       NULL
    ## 47                                               NULL        yes         no
    ## 48                                               NULL       NULL       NULL
    ## 49                                               NULL       NULL       NULL
    ## 50                                               NULL        yes         no
    ## 51                                               NULL       NULL       NULL
    ## 52                                               NULL         no       NULL
    ## 53                                               NULL        yes         no
    ## 54                                               NULL         no       NULL
    ## 55                                               NULL       NULL       NULL
    ## 56                                               NULL        yes         no
    ## 57                                               NULL         no       NULL
    ## 58                                               NULL         no       NULL
    ## 59                                               NULL       NULL       NULL
    ## 60                                               NULL         no       NULL
    ## 61                                               NULL        yes        yes
    ## 62                                               NULL       NULL       NULL
    ## 63                                               NULL       NULL       NULL
    ## 64                                               NULL       NULL       NULL
    ## 65                                               NULL         no       NULL
    ## 66                                               NULL        yes         no
    ## 67                                               NULL         no       NULL
    ## 68                                               NULL         no       NULL
    ## 69                                               NULL         no       NULL
    ## 70                                               NULL         no       NULL
    ## 71                                               NULL        yes         no
    ## 72                                               NULL       NULL       NULL
    ## 73                                               NULL         no       NULL
    ## 74                                               NULL        yes         no
    ## 75                                               NULL       NULL       NULL
    ## 76                                               NULL       NULL       NULL
    ## 77                                               NULL        yes        yes
    ## 78                                               NULL         no       NULL
    ## 79                                               NULL         no       NULL
    ## 80                                               NULL        yes         no
    ## 81                                               NULL         no       NULL
    ## 82                                               NULL         no       NULL
    ## 83                                               NULL        yes         no
    ## 84                                               NULL         no       NULL
    ## 85                                               NULL        yes         no
    ## 86                                               NULL         no       NULL
    ## 87                                               NULL         no       NULL
    ## 88                                               NULL       NULL       NULL
    ## 89                                               NULL        yes         no
    ## 90                                               NULL        yes        yes
    ## 91  ['cheaper' ;  'less_work' ;  'train_outside_org']        yes         no
    ## 92                                               NULL        yes        yes
    ## 93                                               NULL        yes         no
    ## 94                                               NULL         no       NULL
    ## 95                                               NULL         no       NULL
    ## 96                                               NULL         no       NULL
    ## 97                                               NULL         no       NULL
    ## 98                                               NULL        yes        yes
    ## 99                                               NULL         no       NULL
    ## 100                                              NULL         no       NULL
    ## 101                                              NULL        yes         no
    ## 102                                              NULL        yes        yes
    ## 103                                              NULL         no       NULL
    ## 104                                              NULL       NULL       NULL
    ## 105                                              NULL         no       NULL
    ## 106                                              NULL         no       NULL
    ## 107                                              NULL       NULL       NULL
    ## 108                                     ['less_work']         no       NULL
    ## 109                                              NULL         no       NULL
    ## 110                                              NULL       NULL       NULL
    ## 111                                              NULL         no       NULL
    ## 112                                              NULL       NULL       NULL
    ## 113                                              NULL       NULL       NULL
    ## 114                                              NULL         no       NULL
    ## 115                                              NULL         no       NULL
    ## 116                                              NULL         no       NULL
    ## 117                                              NULL         no       NULL
    ## 118                                              NULL        yes        yes
    ## 119                                              NULL         no       NULL
    ## 120                                              NULL         no       NULL
    ## 121                                              NULL         no       NULL
    ## 122                                       ['cheaper']         no       NULL
    ## 123                                              NULL         no       NULL
    ## 124                                              NULL         no       NULL
    ## 125                                              NULL         no       NULL
    ## 126                                              NULL         no       NULL
    ## 127                                              NULL         no       NULL
    ## 128                                              NULL         no       NULL
    ## 129                                              NULL         no       NULL
    ## 130                                              NULL        yes        yes
    ## 131                                              NULL       NULL       NULL
    ##     fees_water affect_conflicts   te need_money                    money_source
    ## 1         NULL             NULL NULL       NULL                            NULL
    ## 2           no             once NULL         no                            NULL
    ## 3         NULL             NULL NULL       NULL                            NULL
    ## 4         NULL             NULL NULL       NULL                            NULL
    ## 5         NULL             NULL NULL       NULL                            NULL
    ## 6         NULL             NULL NULL       NULL                            NULL
    ## 7           no            never NULL         no                            NULL
    ## 8           no            never NULL         no                            NULL
    ## 9           no            never NULL         no                            NULL
    ## 10          no            never NULL         no                            NULL
    ## 11        NULL             NULL NULL       NULL                            NULL
    ## 12          no            never NULL         no                            NULL
    ## 13          no            never NULL         no                            NULL
    ## 14        NULL             NULL NULL       NULL                            NULL
    ## 15          no             once NULL         no                            NULL
    ## 16        NULL             NULL NULL       NULL                            NULL
    ## 17        NULL             NULL NULL       NULL                            NULL
    ## 18        NULL             NULL NULL       NULL                            NULL
    ## 19        NULL             NULL NULL       NULL                            NULL
    ## 20        NULL             NULL NULL       NULL                            NULL
    ## 21          no            never NULL         no                            NULL
    ## 22        NULL             NULL NULL       NULL                            NULL
    ## 23        NULL             NULL NULL       NULL                            NULL
    ## 24          no            never NULL         no                            NULL
    ## 25          no            never NULL        yes ['business' ;  'non_farm_prod']
    ## 26          no            never NULL         no                            NULL
    ## 27        NULL             NULL NULL       NULL                            NULL
    ## 28          no        more_once NULL         no                            NULL
    ## 29          no       frequently NULL         no                            NULL
    ## 30        NULL             NULL NULL       NULL                            NULL
    ## 31        NULL             NULL NULL       NULL                            NULL
    ## 32          no        more_once NULL        yes                     ['farming']
    ## 33          no        more_once NULL         no                            NULL
    ## 34          no        more_once NULL         no                            NULL
    ## 35          no        more_once NULL         no                            NULL
    ## 36          no             once NULL         no                            NULL
    ## 37        NULL             NULL NULL       NULL                            NULL
    ## 38          no            never NULL         no                            NULL
    ## 39        NULL             NULL NULL       NULL                            NULL
    ## 40          no            never NULL         no                            NULL
    ## 41        NULL             NULL NULL       NULL                            NULL
    ## 42          no            never NULL         no                            NULL
    ## 43          no            never NULL         no                            NULL
    ## 44        NULL             NULL NULL       NULL                            NULL
    ## 45          no            never NULL        yes  ['farming' ;  'non_farm_prod']
    ## 46          no             once NULL         no                            NULL
    ## 47          no             once NULL         no                            NULL
    ## 48        NULL             NULL NULL       NULL                            NULL
    ## 49        NULL             NULL NULL       NULL                            NULL
    ## 50          no            never NULL         no                            NULL
    ## 51        NULL             NULL NULL       NULL                            NULL
    ## 52          no            never NULL         no                            NULL
    ## 53          no       frequently NULL         no                            NULL
    ## 54          no            never NULL         no                            NULL
    ## 55        NULL             NULL NULL       NULL                            NULL
    ## 56          no            never NULL         no                            NULL
    ## 57          no            never NULL         no                            NULL
    ## 58          no            never NULL         no                            NULL
    ## 59        NULL             NULL NULL       NULL                            NULL
    ## 60          no            never NULL         no                            NULL
    ## 61          no        more_once NULL         no                            NULL
    ## 62        NULL             NULL NULL       NULL                            NULL
    ## 63        NULL             NULL NULL       NULL                            NULL
    ## 64        NULL             NULL NULL       NULL                            NULL
    ## 65          no             once NULL         no                            NULL
    ## 66          no       frequently NULL         no                            NULL
    ## 67          no        more_once NULL         no                            NULL
    ## 68          no        more_once NULL         no                            NULL
    ## 69          no        more_once NULL         no                            NULL
    ## 70          no        more_once NULL         no                            NULL
    ## 71          no        more_once NULL         no                            NULL
    ## 72        NULL             NULL NULL       NULL                            NULL
    ## 73          no            never NULL         no                            NULL
    ## 74          no             once NULL         no                            NULL
    ## 75        NULL             NULL NULL       NULL                            NULL
    ## 76        NULL             NULL NULL       NULL                            NULL
    ## 77          no       frequently NULL         no                            NULL
    ## 78          no        more_once NULL         no                            NULL
    ## 79          no            never NULL         no                            NULL
    ## 80          no        more_once NULL         no                            NULL
    ## 81          no        more_once NULL         no                            NULL
    ## 82          no        more_once NULL         no                            NULL
    ## 83          no        more_once NULL         no                            NULL
    ## 84          no            never NULL         no                            NULL
    ## 85          no        more_once NULL         no                            NULL
    ## 86          no        more_once NULL         no                            NULL
    ## 87          no            never NULL         no                            NULL
    ## 88        NULL             NULL NULL       NULL                            NULL
    ## 89          no        more_once NULL         no                            NULL
    ## 90          no        more_once NULL         no                            NULL
    ## 91          no        more_once NULL         no                            NULL
    ## 92          no        more_once NULL         no                            NULL
    ## 93          no            never NULL         no                            NULL
    ## 94          no            never NULL         no                            NULL
    ## 95          no            never NULL         no                            NULL
    ## 96          no            never NULL         no                            NULL
    ## 97          no            never NULL         no                            NULL
    ## 98          no       frequently NULL         no                            NULL
    ## 99          no        more_once NULL         no                            NULL
    ## 100         no        more_once NULL         no                            NULL
    ## 101         no            never NULL         no                            NULL
    ## 102         no       frequently NULL         no                            NULL
    ## 103         no            never NULL         no                            NULL
    ## 104       NULL             NULL NULL       NULL                            NULL
    ## 105         no            never NULL         no                            NULL
    ## 106         no            never NULL         no                            NULL
    ## 107       NULL             NULL NULL       NULL                            NULL
    ## 108         no        more_once NULL         no                            NULL
    ## 109         no            never NULL         no                            NULL
    ## 110       NULL             NULL NULL       NULL                            NULL
    ## 111         no            never NULL         no                            NULL
    ## 112       NULL             NULL NULL       NULL                            NULL
    ## 113       NULL             NULL NULL       NULL                            NULL
    ## 114        yes       frequently NULL        yes                     ['farming']
    ## 115         no       frequently NULL         no                            NULL
    ## 116         no            never NULL         no                            NULL
    ## 117         no            never NULL         no                            NULL
    ## 118         no       frequently NULL         no                            NULL
    ## 119         no            never NULL         no                            NULL
    ## 120         no            never NULL         no                            NULL
    ## 121         no            never NULL         no                            NULL
    ## 122         no            never NULL         no                            NULL
    ## 123         no            never NULL         no                            NULL
    ## 124         no            never NULL         no                            NULL
    ## 125         no            never NULL         no                            NULL
    ## 126         no             once NULL         no                            NULL
    ## 127         no        more_once NULL         no                            NULL
    ## 128         no        more_once NULL         no                            NULL
    ## 129         no        more_once NULL         no                            NULL
    ## 130         no        more_once NULL        yes       ['farming' ;  'business']
    ## 131       NULL             NULL NULL       NULL                            NULL
    ##     money_source_other crops_contr emply_lab du_labour
    ## 1                 NULL        NULL        no        no
    ## 2                 NULL   more_half       yes        no
    ## 3                 NULL        NULL        no       yes
    ## 4                 NULL        NULL        no       yes
    ## 5                 NULL        NULL        no        no
    ## 6                 NULL        NULL        no       yes
    ## 7                 NULL   more_half        no        no
    ## 8                 NULL    abt_half       yes        no
    ## 9                 NULL   more_half       yes       yes
    ## 10                NULL   more_half       yes        no
    ## 11                NULL        NULL        no       yes
    ## 12                NULL   more_half        no        no
    ## 13                NULL   more_half       yes        no
    ## 14                NULL        NULL       yes       yes
    ## 15                NULL    abt_half        no        no
    ## 16                NULL        NULL       yes       yes
    ## 17                NULL        NULL        no       yes
    ## 18                NULL        NULL        no       yes
    ## 19                NULL        NULL       yes       yes
    ## 20                NULL        NULL        no       yes
    ## 21                NULL   less_half        no       yes
    ## 22                NULL        NULL        no       yes
    ## 23                NULL        NULL       yes        no
    ## 24                NULL   less_half       yes        no
    ## 25                NULL   more_half       yes        no
    ## 26                NULL    abt_half       yes       yes
    ## 27                NULL        NULL        no        no
    ## 28                NULL   more_half        no       yes
    ## 29                NULL   more_half        no        no
    ## 30                NULL        NULL        no       yes
    ## 31                NULL        NULL        no        no
    ## 32                NULL   more_half       yes       yes
    ## 33                NULL   more_half        no        no
    ## 34                NULL   more_half        no        no
    ## 35                NULL   more_half        no       yes
    ## 36                NULL    abt_half       yes       yes
    ## 37                NULL        NULL        no        no
    ## 38                NULL   more_half        no       yes
    ## 39                NULL        NULL        no        no
    ## 40                NULL   more_half        no        no
    ## 41                NULL        NULL        no        no
    ## 42                NULL   less_half        no        no
    ## 43                NULL    abt_half       yes        no
    ## 44                NULL        NULL       yes        no
    ## 45                NULL   more_half       yes        no
    ## 46                NULL   more_half       yes        no
    ## 47                NULL   more_half        no        no
    ## 48                NULL        NULL        no        no
    ## 49                NULL        NULL        no       yes
    ## 50                NULL    abt_half       yes        no
    ## 51                NULL        NULL        no       yes
    ## 52                NULL   less_half        no        no
    ## 53                NULL   more_half        no        no
    ## 54                NULL   more_half        no        no
    ## 55                NULL        NULL        no        no
    ## 56                NULL   more_half        no        no
    ## 57                NULL   less_half        no        no
    ## 58                NULL   more_half        no        no
    ## 59                NULL        NULL        no        no
    ## 60                NULL   more_half       yes       yes
    ## 61                NULL   more_half       yes        no
    ## 62                NULL        NULL        no       yes
    ## 63                NULL        NULL        no       yes
    ## 64                NULL        NULL        no        no
    ## 65                NULL    abt_half        no        no
    ## 66                NULL   more_half       yes        no
    ## 67                NULL   more_half       yes       yes
    ## 68                NULL   more_half        no        no
    ## 69                NULL   more_half        no        no
    ## 70                NULL   more_half        no       yes
    ## 71                NULL   more_half        no       yes
    ## 72                NULL        NULL        no        no
    ## 73                NULL    abt_half        no       yes
    ## 74                NULL    abt_half        no        no
    ## 75                NULL        NULL        no       yes
    ## 76                NULL        NULL       yes        no
    ## 77                NULL    abt_half       yes       yes
    ## 78                NULL   more_half       yes        no
    ## 79                NULL    abt_half        no       yes
    ## 80                NULL   more_half        no        no
    ## 81                NULL   more_half        no        no
    ## 82                NULL   more_half        no        no
    ## 83                NULL   more_half        no        no
    ## 84                NULL   more_half       yes        no
    ## 85                NULL   more_half        no        no
    ## 86                NULL   more_half       yes        no
    ## 87                NULL   less_half       yes        no
    ## 88                NULL        NULL        no       yes
    ## 89                NULL   more_half        no       yes
    ## 90                NULL   more_half        no       yes
    ## 91                NULL   more_half       yes        no
    ## 92                NULL   more_half        no        no
    ## 93                NULL    abt_half        no        no
    ## 94                NULL    abt_half       yes       yes
    ## 95                NULL   less_half        no       yes
    ## 96                NULL    abt_half        no       yes
    ## 97                NULL   less_half       yes        no
    ## 98                NULL   less_half        no       yes
    ## 99                NULL    abt_half        no        no
    ## 100               NULL   more_half        no       yes
    ## 101               NULL    abt_half        no        no
    ## 102               NULL   more_half        no       yes
    ## 103               NULL   more_half       yes        no
    ## 104               NULL        NULL        no        no
    ## 105               NULL    abt_half        no        no
    ## 106               NULL   less_half       yes        no
    ## 107               NULL        NULL        no       yes
    ## 108               NULL   less_half       yes       yes
    ## 109               NULL   more_half        no        no
    ## 110               NULL        NULL       yes        no
    ## 111               NULL    abt_half        no        no
    ## 112               NULL        NULL        no       yes
    ## 113               NULL        NULL        no       yes
    ## 114               NULL    abt_half        no        no
    ## 115               NULL   more_half       yes        no
    ## 116               NULL   less_half        no       yes
    ## 117               NULL   less_half        no       yes
    ## 118               NULL   more_half       yes       yes
    ## 119               NULL   less_half        no        no
    ## 120               NULL   less_half        no       yes
    ## 121               NULL   less_half        no       yes
    ## 122               NULL   more_half       yes        no
    ## 123               NULL   more_half        no        no
    ## 124               NULL   more_half        no       yes
    ## 125               NULL    abt_half        no        no
    ## 126               NULL   more_half       yes       yes
    ## 127               NULL   less_half       yes       yes
    ## 128               NULL   more_half        no       yes
    ## 129               NULL   more_half        no       yes
    ## 130               NULL   more_half       yes        no
    ## 131               NULL        NULL        no       yes
    ##                                                 liv_owned liv_owned_other
    ## 1                                             ['poultry']            NULL
    ## 2                           ['oxen' ;  'cows' ;  'goats']            NULL
    ## 3                                                ['none']            NULL
    ## 4                                      ['oxen' ;  'cows']            NULL
    ## 5              ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 6                                                ['none']            NULL
    ## 7                                                ['oxen']            NULL
    ## 8                                     ['oxen' ;  'goats']            NULL
    ## 9                           ['oxen' ;  'cows' ;  'goats']            NULL
    ## 10                                     ['oxen' ;  'cows']            NULL
    ## 11                                     ['oxen' ;  'cows']            NULL
    ## 12                                     ['oxen' ;  'cows']            NULL
    ## 13                       ['cows' ;  'goats' ;  'poultry']            NULL
    ## 14                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 15                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 16             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 17                                              ['goats']            NULL
    ## 18                       ['goats' ;  'pigs' ;  'poultry']            NULL
    ## 19                                    ['oxen' ;  'goats']            NULL
    ## 20                                               ['cows']            NULL
    ## 21                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 22                                              ['goats']            NULL
    ## 23                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 24                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 25                                     ['oxen' ;  'cows']            NULL
    ## 26                                     ['oxen' ;  'cows']            NULL
    ## 27                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 28                                               ['none']            NULL
    ## 29                                              ['goats']            NULL
    ## 30                                               ['none']            NULL
    ## 31                                               ['none']            NULL
    ## 32   ['oxen' ;  'cows' ;  'goats' ;  'pigs' ;  'poultry']            NULL
    ## 33                                  ['oxen' ;  'poultry']            NULL
    ## 34                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 35                                     ['oxen' ;  'cows']            NULL
    ## 36                           ['oxen' ;  'cows' ;  'pigs']            NULL
    ## 37                                     ['oxen' ;  'cows']            NULL
    ## 38                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 39                                               ['oxen']            NULL
    ## 40                                               ['oxen']            NULL
    ## 41                                  ['oxen' ;  'poultry']            NULL
    ## 42                       ['cows' ;  'goats' ;  'poultry']            NULL
    ## 43                                     ['oxen' ;  'cows']            NULL
    ## 44                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 45             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 46                                  ['oxen' ;  'poultry']            NULL
    ## 47                                               ['none']            NULL
    ## 48                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 49                                 ['goats' ;  'poultry']            NULL
    ## 50                                            ['poultry']            NULL
    ## 51                                            ['poultry']            NULL
    ## 52                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 53                                    ['oxen' ;  'goats']            NULL
    ## 54                                               ['none']            NULL
    ## 55                                              ['goats']            NULL
    ## 56                                    ['oxen' ;  'goats']            NULL
    ## 57                                               ['none']            NULL
    ## 58                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 59                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 60             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 61                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 62                                               ['none']            NULL
    ## 63                                               ['none']            NULL
    ## 64                                              ['goats']            NULL
    ## 65                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 66             ['oxen' ;  'cows' ;  'goats' ;  'donkeys']            NULL
    ## 67             ['oxen' ;  'cows' ;  'goats' ;  'donkeys']            NULL
    ## 68                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 69                                              ['goats']            NULL
    ## 70             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 71                       ['oxen' ;  'goats' ;  'poultry']            NULL
    ## 72                                               ['pigs']            NULL
    ## 73  ['oxen' ;  'cows' ;  'goats' ;  'sheep' ;  'poultry']            NULL
    ## 74                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 75                                              ['goats']            NULL
    ## 76                                               ['none']            NULL
    ## 77                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 78                                     ['oxen' ;  'cows']            NULL
    ## 79                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 80                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 81                                     ['oxen' ;  'cows']            NULL
    ## 82                                     ['oxen' ;  'cows']            NULL
    ## 83             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 84                        ['oxen' ;  'cows' ;  'poultry']            NULL
    ## 85                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 86                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 87                                               ['none']            NULL
    ## 88                                     ['oxen' ;  'cows']            NULL
    ## 89                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 90                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 91                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 92             ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 93                                     ['oxen' ;  'cows']            NULL
    ## 94                                     ['oxen' ;  'cows']            NULL
    ## 95                          ['oxen' ;  'cows' ;  'goats']            NULL
    ## 96                                              ['goats']            NULL
    ## 97   ['oxen' ;  'cows' ;  'goats' ;  'pigs' ;  'poultry']            NULL
    ## 98                                    ['cows' ;  'goats']            NULL
    ## 99                                     ['oxen' ;  'cows']            NULL
    ## 100                                              ['none']            NULL
    ## 101               ['oxen' ;  'cows' ;  'goats' ;  'pigs']            NULL
    ## 102                                 ['cows' ;  'poultry']            NULL
    ## 103                                    ['oxen' ;  'cows']            NULL
    ## 104                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 105                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 106            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 107                                              ['none']            NULL
    ## 108                                    ['oxen' ;  'cows']            NULL
    ## 109            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 110                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 111            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 112                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 113                                              ['none']            NULL
    ## 114              ['oxen' ;  'cows' ;  'goats' ;  'sheep']            NULL
    ## 115                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 116                                              ['cows']            NULL
    ## 117                                              ['none']            NULL
    ## 118                                    ['oxen' ;  'cows']            NULL
    ## 119                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 120                                             ['goats']            NULL
    ## 121                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 122                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 123            ['oxen' ;  'cows' ;  'goats' ;  'poultry']            NULL
    ## 124                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 125                                              ['cows']            NULL
    ## 126                                              ['none']            NULL
    ## 127                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 128                         ['oxen' ;  'cows' ;  'goats']            NULL
    ## 129                                           ['poultry']            NULL
    ## 130                                    ['oxen' ;  'cows']            NULL
    ## 131                         ['oxen' ;  'goats' ;  'pigs']            NULL
    ##     v_count poultry du_look_aftr_cows
    ## 1         1     yes                no
    ## 2         3     yes                no
    ## 3         1     yes                no
    ## 4         2     yes                no
    ## 5         4     yes                no
    ## 6         1      no                no
    ## 7         1      no                no
    ## 8         2     yes                no
    ## 9         3     yes                no
    ## 10        2     yes                no
    ## 11        2      no                no
    ## 12        2     yes                no
    ## 13        3     yes                no
    ## 14        3     yes                no
    ## 15        3     yes                no
    ## 16        4      no                no
    ## 17        1      no               yes
    ## 18        3     yes                no
    ## 19        2     yes                no
    ## 20        1     yes               yes
    ## 21        3     yes                no
    ## 22        1     yes                no
    ## 23        3     yes                no
    ## 24        3      no                no
    ## 25        2     yes                no
    ## 26        2     yes                no
    ## 27        3     yes                no
    ## 28        1     yes                no
    ## 29        1     yes                no
    ## 30        1      no                no
    ## 31        1      no                no
    ## 32        5     yes                no
    ## 33        2     yes                no
    ## 34        3     yes                no
    ## 35        2     yes                no
    ## 36        3      no                no
    ## 37        2     yes                no
    ## 38        3     yes               yes
    ## 39        1     yes                no
    ## 40        1     yes                no
    ## 41        2      no                no
    ## 42        3     yes                no
    ## 43        2      no                no
    ## 44        3     yes                no
    ## 45        4      no                no
    ## 46        2      no                no
    ## 47        1      no                no
    ## 48        3     yes                no
    ## 49        2     yes                no
    ## 50        1     yes                no
    ## 51        1      no                no
    ## 52        3     yes                no
    ## 53        2     yes                no
    ## 54        1     yes                no
    ## 55        1     yes                no
    ## 56        2     yes                no
    ## 57        1      no                no
    ## 58        3      no                no
    ## 59        3      no                no
    ## 60        4     yes                no
    ## 61        3     yes                no
    ## 62        1      no                no
    ## 63        1      no                no
    ## 64        1     yes                no
    ## 65        3     yes                no
    ## 66        4     yes                no
    ## 67        4     yes                no
    ## 68        3     yes                no
    ## 69        1     yes                no
    ## 70        4      no                no
    ## 71        3      no                no
    ## 72        1      no                no
    ## 73        5     yes                no
    ## 74        3     yes               yes
    ## 75        1     yes                no
    ## 76        1     yes                no
    ## 77        3      no                no
    ## 78        2     yes                no
    ## 79        3     yes                no
    ## 80        3     yes                no
    ## 81        2     yes                no
    ## 82        2      no                no
    ## 83        4     yes                no
    ## 84        3      no                no
    ## 85        3     yes                no
    ## 86        3     yes               yes
    ## 87        1     yes                no
    ## 88        2     yes                no
    ## 89        3     yes                no
    ## 90        3     yes                no
    ## 91        3     yes                no
    ## 92        4     yes                no
    ## 93        2      no                no
    ## 94        2     yes                no
    ## 95        3      no                no
    ## 96        1      no               yes
    ## 97        5     yes                no
    ## 98        2      no                no
    ## 99        2      no                no
    ## 100       1     yes                no
    ## 101       4     yes                no
    ## 102       2     yes               yes
    ## 103       2     yes                no
    ## 104       3     yes                no
    ## 105       3     yes                no
    ## 106       4      no                no
    ## 107       1     yes                no
    ## 108       2      no               yes
    ## 109       4      no                no
    ## 110       3     yes                no
    ## 111       4     yes                no
    ## 112       3     yes                no
    ## 113       1     yes                no
    ## 114       4     yes                no
    ## 115       3     yes                no
    ## 116       1      no               yes
    ## 117       1      no                no
    ## 118       2     yes                no
    ## 119       3     yes                no
    ## 120       1     yes                no
    ## 121       3     yes               yes
    ## 122       3     yes                no
    ## 123       4     yes               yes
    ## 124       3     yes                no
    ## 125       1     yes                no
    ## 126       1     yes                no
    ## 127       3     yes                no
    ## 128       3      no                no
    ## 129       1      no                no
    ## 130       2     yes                no
    ## 131       3     yes                no
    ##                                                                                                                                                                                                            items_owned
    ## 1                                                                                                                                                              ['bicycle' ;  'television' ;  'solar_panel' ;  'table']
    ## 2                                                                                                  ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 3                                                                                                                                                                                                      ['solar_torch']
    ## 4                                                                                                                                            ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 5                                                                                                                                                           ['motorcyle' ;  'radio' ;  'cow_plough' ;  'mobile_phone']
    ## 6                                                                                                                                                                                                                 NULL
    ## 7                                                                                                                                                                                        ['motorcyle' ;  'cow_plough']
    ## 8                                                                                       ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'fridge']
    ## 9                                                                                                                                                                     ['television' ;  'solar_panel' ;  'solar_torch']
    ## 10                                                                                    ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table']
    ## 11                                                                                                                                                                                           ['radio' ;  'cow_plough']
    ## 12                                                                                                                                                     ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 13                                                                                                                                                            ['bicycle' ;  'radio' ;  'cow_plough' ;  'mobile_phone']
    ## 14                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 15                                                                                                                                                  ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table']
    ## 16                                                                                                                                                         ['radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch']
    ## 17                                                                                                                                                                                                    ['mobile_phone']
    ## 18                                                                                                                                                                                       ['bicycle' ;  'mobile_phone']
    ## 19                                                                                                                          ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 20                                                                                                                                                                        ['bicycle' ;  'cow_plough' ;  'solar_torch']
    ## 21                                                                                                                                                                                                                NULL
    ## 22                                                                                                                                                                                                           ['radio']
    ## 23                                                                                            ['cow_cart' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'electricity' ;  'mobile_phone']
    ## 24                                                                                                                                                                ['radio' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 25                                                                 ['cow_cart' ;  'motorcyle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 26                                                                                                                                                              ['radio' ;  'cow_plough' ;  'table' ;  'mobile_phone']
    ## 27                                                                                                                          ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 28                                                                                                                                                                                                                NULL
    ## 29                                                                                                                                                  ['motorcyle' ;  'bicycle' ;  'radio' ;  'table' ;  'mobile_phone']
    ## 30                                                                                                                                                                            ['bicycle' ;  'radio' ;  'mobile_phone']
    ## 31                                                                                                                                                                                                                NULL
    ## 32                                                                                                                           ['cow_cart' ;  'motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 33                                                                                                               ['cow_cart' ;  'lorry' ;  'motorcyle' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 34                                                                                                            ['television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 35                                                                                                                                                                                         ['bicycle' ;  'cow_plough']
    ## 36                                                                                                                             ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 37                                                                                                          ['bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 38                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 39                                                                                                                                                                                                                NULL
    ## 40                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 41                                                                                                                                                    ['motorcyle' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 42                                                                                                                                                                                                    ['mobile_phone']
    ## 43                                                                                                                                                                                    ['cow_plough' ;  'mobile_phone']
    ## 44                                                                                                                                                                                          ['radio' ;  'solar_torch']
    ## 45                                                                                ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 46                                                                                              ['motorcyle' ;  'computer' ;  'television' ;  'sterio' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 47                                                                                                                                                                                   ['solar_torch' ;  'mobile_phone']
    ## 48                                                                                                                                                                                                           ['radio']
    ## 49                                                                                                               ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 50                                                                                                                                                                                                     ['solar_torch']
    ## 51                                                                                                                                                                                                           ['radio']
    ## 52                                                                                                                         ['motorcyle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 53                                                                                                                                                                            ['bicycle' ;  'radio' ;  'mobile_phone']
    ## 54                                                                                                                                                                                                                NULL
    ## 55                                                                                                                                                                    ['television' ;  'cow_plough' ;  'mobile_phone']
    ## 56                                                                                                                                                                        ['motorcyle' ;  'bicycle' ;  'mobile_phone']
    ## 57                                                                                                                                                                                                           ['radio']
    ## 58                                                                                                            ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 59                                                                                                                                                                                                                NULL
    ## 60                                                                                                                                                                                                      ['cow_plough']
    ## 61                                                                                   ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 62                                                                                                                                                                            ['bicycle' ;  'radio' ;  'mobile_phone']
    ## 63                                                                                                                                                                                                                NULL
    ## 64                                                                                                                                             ['bicycle' ;  'solar_torch' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 65                                                                                                                                                                 ['motorcyle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 66                                                                             ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 67                                                                                                                                         ['motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 68                                                                                                                                        ['motorcyle' ;  'television' ;  'sterio' ;  'solar_panel' ;  'mobile_phone']
    ## 69                                                                                                                                                           ['bicycle' ;  'radio' ;  'solar_torch' ;  'mobile_phone']
    ## 70                                                                                                                             ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 71                                                                                                                                                                         ['radio' ;  'cow_plough' ;  'mobile_phone']
    ## 72                                                                                                                                                                                                    ['mobile_phone']
    ## 73  ['cow_cart' ;  'car' ;  'lorry' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'electricity' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 74                                                                                                                ['motorcyle' ;  'bicycle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 75                                                                                                                                                                                                                NULL
    ## 76                                                                                                                                                                                                     ['electricity']
    ## 77                                                                                                                                                        ['radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 78                                                                                                                                    ['motorcyle' ;  'television' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 79                                                                                                                                                                                     ['cow_plough' ;  'solar_panel']
    ## 80                                                                                              ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 81                                                                                                                                                                                                     ['solar_panel']
    ## 82                                                                                                                                                                                    ['cow_plough' ;  'mobile_phone']
    ## 83                                                                             ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 84                                                                                                                                               ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_torch']
    ## 85                                                                                                                                                                         ['radio' ;  'cow_plough' ;  'mobile_phone']
    ## 86                                                                                                                ['bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 87                                                                                                                                                                                                                NULL
    ## 88                                                                                                                                                           ['bicycle' ;  'radio' ;  'solar_torch' ;  'mobile_phone']
    ## 89                                                                                                              ['cow_cart' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 90                                                                                                                                                                              ['bicycle' ;  'radio' ;  'cow_plough']
    ## 91                                                                                   ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 92                                                                                                                                           ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 93                                                                                                                                                                          ['radio' ;  'cow_plough' ;  'solar_torch']
    ## 94                                                                                                                                                                                           ['radio' ;  'cow_plough']
    ## 95                                                                                                               ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 96                                                                                                                                                                                        ['bicycle' ;  'solar_torch']
    ## 97                                                                                                                                       ['cow_cart' ;  'cow_plough' ;  'solar_panel' ;  'sofa_set' ;  'mobile_phone']
    ## 98                                                                                                                                                           ['cow_plough' ;  'table' ;  'sofa_set' ;  'mobile_phone']
    ## 99                                                                                                                                                                                                      ['cow_plough']
    ## 100                                                                                                                             ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch']
    ## 101                                                                                                                                                                          ['cow_cart' ;  'bicycle' ;  'cow_plough']
    ## 102                                                                                                                                        ['motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 103                                                                     ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 104                                                                                                                                                    ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'table']
    ## 105                                                                                                                                                ['bicycle' ;  'radio' ;  'cow_plough' ;  'table' ;  'mobile_phone']
    ## 106                                                                                 ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 107                                                                                                                                                                       ['radio' ;  'solar_torch' ;  'mobile_phone']
    ## 108                                                                                                                         ['bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 109                                                                                                                                                     ['bicycle' ;  'cow_plough' ;  'solar_panel' ;  'mobile_phone']
    ## 110                                                                 ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 111                                                                                                                 ['cow_cart' ;  'bicycle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 112                                                                               ['motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 113                                                                                                            ['motorcyle' ;  'television' ;  'radio' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 114                                                                                             ['cow_cart' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 115                                                                                               ['cow_cart' ;  'motorcyle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 116                                                                                                                                                                                                   ['mobile_phone']
    ## 117                                                                                                                                                                        ['radio' ;  'solar_panel' ;  'solar_torch']
    ## 118                                                                                                                                                    ['cow_cart' ;  'cow_plough' ;  'solar_torch' ;  'mobile_phone']
    ## 119                                       ['cow_cart' ;  'motorcyle' ;  'bicycle' ;  'television' ;  'radio' ;  'cow_plough' ;  'solar_torch' ;  'electricity' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 120                                                                                                                                                                     ['bicycle' ;  'solar_torch' ;  'mobile_phone']
    ## 121                                                                                                            ['motorcyle' ;  'radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 122                                                  ['car' ;  'lorry' ;  'motorcyle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 123                                                                                                    ['motorcyle' ;  'bicycle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 124                                                                                                                 ['motorcyle' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'table' ;  'mobile_phone']
    ## 125                                                                                                                                      ['radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 126                                                                                                  ['bicycle' ;  'television' ;  'radio' ;  'sterio' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ## 127                                                                                                                                                                          ['motorcyle' ;  'radio' ;  'solar_panel']
    ## 128                                                 ['car' ;  'lorry' ;  'television' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_torch' ;  'electricity' ;  'table' ;  'sofa_set' ;  'mobile_phone' ;  'fridge']
    ## 129                                                                                                                                                      ['radio' ;  'solar_panel' ;  'solar_torch' ;  'mobile_phone']
    ## 130                                   ['cow_cart' ;  'lorry' ;  'motorcyle' ;  'computer' ;  'television' ;  'radio' ;  'sterio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'electricity' ;  'mobile_phone']
    ## 131                                                                                                                           ['radio' ;  'cow_plough' ;  'solar_panel' ;  'solar_torch' ;  'table' ;  'mobile_phone']
    ##     items_owned_other no_meals
    ## 1                NULL        2
    ## 2                NULL        2
    ## 3                NULL        2
    ## 4                NULL        2
    ## 5                NULL        2
    ## 6                NULL        2
    ## 7                NULL        3
    ## 8                NULL        2
    ## 9                NULL        3
    ## 10               NULL        3
    ## 11               NULL        2
    ## 12               NULL        3
    ## 13               NULL        2
    ## 14               NULL        3
    ## 15               NULL        2
    ## 16               NULL        3
    ## 17               NULL        2
    ## 18               NULL        2
    ## 19               NULL        3
    ## 20               NULL        2
    ## 21               NULL        2
    ## 22               NULL        2
    ## 23               NULL        3
    ## 24               NULL        2
    ## 25               NULL        2
    ## 26               NULL        2
    ## 27               NULL        3
    ## 28               NULL        3
    ## 29               NULL        3
    ## 30               NULL        2
    ## 31               NULL        3
    ## 32               NULL        2
    ## 33               NULL        2
    ## 34               NULL        2
    ## 35               NULL        3
    ## 36               NULL        3
    ## 37               NULL        3
    ## 38               NULL        3
    ## 39               NULL        3
    ## 40               NULL        3
    ## 41               NULL        3
    ## 42               NULL        3
    ## 43               NULL        2
    ## 44               NULL        2
    ## 45               NULL        3
    ## 46               NULL        2
    ## 47               NULL        3
    ## 48               NULL        3
    ## 49               NULL        3
    ## 50               NULL        2
    ## 51               NULL        3
    ## 52               NULL        3
    ## 53               NULL        2
    ## 54               NULL        2
    ## 55               NULL        2
    ## 56               NULL        3
    ## 57               NULL        2
    ## 58               NULL        2
    ## 59               NULL        2
    ## 60               NULL        2
    ## 61               NULL        3
    ## 62               NULL        3
    ## 63               NULL        3
    ## 64               NULL        3
    ## 65               NULL        3
    ## 66               NULL        3
    ## 67               NULL        3
    ## 68               NULL        3
    ## 69               NULL        3
    ## 70               NULL        2
    ## 71               NULL        2
    ## 72               NULL        2
    ## 73               NULL        3
    ## 74               NULL        3
    ## 75               NULL        2
    ## 76               NULL        2
    ## 77               NULL        3
    ## 78               NULL        3
    ## 79               NULL        3
    ## 80               NULL        3
    ## 81               NULL        3
    ## 82               NULL        3
    ## 83               NULL        3
    ## 84               NULL        2
    ## 85               NULL        3
    ## 86               NULL        2
    ## 87               NULL        3
    ## 88               NULL        2
    ## 89               NULL        3
    ## 90               NULL        2
    ## 91               NULL        3
    ## 92               NULL        3
    ## 93               NULL        2
    ## 94               NULL        2
    ## 95               NULL        3
    ## 96               NULL        3
    ## 97               NULL        3
    ## 98               NULL        3
    ## 99               NULL        2
    ## 100              NULL        3
    ## 101              NULL        3
    ## 102              NULL        3
    ## 103              NULL        3
    ## 104              NULL        3
    ## 105              NULL        2
    ## 106              NULL        3
    ## 107              NULL        3
    ## 108              NULL        3
    ## 109              NULL        3
    ## 110              NULL        3
    ## 111              NULL        3
    ## 112              NULL        3
    ## 113              NULL        3
    ## 114              NULL        2
    ## 115              NULL        3
    ## 116              NULL        3
    ## 117              NULL        3
    ## 118              NULL        2
    ## 119              NULL        3
    ## 120              NULL        2
    ## 121              NULL        2
    ## 122              NULL        3
    ## 123              NULL        2
    ## 124              NULL        3
    ## 125              NULL        2
    ## 126              NULL        3
    ## 127              NULL        3
    ## 128              NULL        3
    ## 129              NULL        3
    ## 130              NULL        3
    ## 131              NULL        3
    ##                                                                                         months_lack_food
    ## 1                                                                                                ['Jan']
    ## 2                                                           ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 3                                                   ['Jan' ;  'Feb' ;  'Mar' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 4                                                                    ['Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 5                                                                    ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 6                                                                             ['Aug' ;  'Sept' ;  'Oct']
    ## 7                                                                                                ['Nov']
    ## 8                                                                                                ['Jan']
    ## 9                                                                                       ['Jan' ;  'Dec']
    ## 10                                                                    ['Jan' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 11                                                                                      ['Oct' ;  'Nov']
    ## 12                                                                                     ['Sept' ;  'Oct']
    ## 13                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 14                                               ['June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 15  ['Jan' ;  'Feb' ;  'Mar' ;  'Apr' ;  'May' ;  'June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 16                                                                                      ['Jan' ;  'Feb']
    ## 17                                                                                      ['Nov' ;  'Dec']
    ## 18                                                                                      ['Oct' ;  'Nov']
    ## 19                                                                             ['Oct' ;  'Nov' ;  'Dec']
    ## 20                                                                                      ['Oct' ;  'Nov']
    ## 21                                                  ['Jan' ;  'Feb' ;  'Mar' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 22                      ['Jan' ;  'Feb' ;  'Mar' ;  'Apr' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 23                                                                                              ['none']
    ## 24                                                                                      ['Nov' ;  'Dec']
    ## 25                                                                             ['Jan' ;  'Feb' ;  'Oct']
    ## 26                                                                                              ['none']
    ## 27                                                                                              ['none']
    ## 28                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 29                                                                                      ['Jan' ;  'Feb']
    ## 30                                                                                      ['Jan' ;  'Feb']
    ## 31                                                                                              ['none']
    ## 32                                                                                              ['none']
    ## 33                                                                                              ['none']
    ## 34                                                                                      ['Jan' ;  'Dec']
    ## 35                                                          ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 36                                                                                              ['none']
    ## 37                                                                             ['Jan' ;  'Nov' ;  'Dec']
    ## 38                                                                                               ['Nov']
    ## 39                                                                                               ['Nov']
    ## 40                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 41                                                                                      ['Oct' ;  'Nov']
    ## 42                                                                             ['Jan' ;  'Nov' ;  'Dec']
    ## 43                                                           ['Jan' ;  'Feb' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 44                                                                                      ['Jan' ;  'Dec']
    ## 45                                                                                              ['none']
    ## 46                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 47                                                                                              ['none']
    ## 48                                               ['June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 49                                                                             ['Jan' ;  'Nov' ;  'Dec']
    ## 50                                      ['June' ;  'July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 51                                                                                      ['Oct' ;  'Nov']
    ## 52                                                                   ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 53                                                                                               ['Nov']
    ## 54                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 55                                                                                      ['Oct' ;  'Nov']
    ## 56                                                                                              ['none']
    ## 57                                                                                              ['none']
    ## 58                                                                                              ['none']
    ## 59                                                                                              ['none']
    ## 60                                                                                              ['none']
    ## 61                                                                             ['Jan' ;  'Feb' ;  'Dec']
    ## 62                                                                   ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 63                                                                    ['Jan' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 64                                                                             ['Jan' ;  'Feb' ;  'Dec']
    ## 65                                                                             ['Jan' ;  'Feb' ;  'Mar']
    ## 66                                                                                              ['none']
    ## 67                                                                                              ['none']
    ## 68                                                                                              ['none']
    ## 69                                                                                              ['none']
    ## 70                                                                                              ['none']
    ## 71                                                                   ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 72                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 73                                                                             ['Jan' ;  'Oct' ;  'Nov']
    ## 74                                                                                              ['none']
    ## 75                                                                                      ['Oct' ;  'Nov']
    ## 76                                                          ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 77                                                                                              ['none']
    ## 78                                                                                               ['Nov']
    ## 79                                                                                      ['Oct' ;  'Nov']
    ## 80                                                                                              ['none']
    ## 81                                                                    ['Jan' ;  'Feb' ;  'Nov' ;  'Dec']
    ## 82                                                                                              ['none']
    ## 83                                                                                              ['none']
    ## 84                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 85                                                                                              ['none']
    ## 86                                                                                               ['Nov']
    ## 87                                                                                               ['Nov']
    ## 88                                                                             ['Oct' ;  'Nov' ;  'Dec']
    ## 89                                                  ['Jan' ;  'Feb' ;  'Mar' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 90                                                 ['Jan' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 91                                                                            ['Jan' ;  'Sept' ;  'Oct']
    ## 92                                                                                              ['none']
    ## 93                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 94                                                                                      ['Oct' ;  'Nov']
    ## 95                                                                                      ['Oct' ;  'Nov']
    ## 96                                                                            ['Sept' ;  'Oct' ;  'Nov']
    ## 97                                                                             ['Jan' ;  'Feb' ;  'Dec']
    ## 98                                                                                      ['Jan' ;  'Feb']
    ## 99                                                                            ['Aug' ;  'Sept' ;  'Oct']
    ## 100                                                                                             ['none']
    ## 101                                                                            ['Jan' ;  'Feb' ;  'Dec']
    ## 102                                                                            ['Jan' ;  'Feb' ;  'Dec']
    ## 103                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 104                                                        ['July' ;  'Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 105                                                                                             ['none']
    ## 106                                                                                             ['none']
    ## 107                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 108                                                         ['Jan' ;  'Sept' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 109                                                                                             ['none']
    ## 110                                                                                             ['none']
    ## 111                                                                  ['Aug' ;  'Sept' ;  'Oct' ;  'Nov']
    ## 112                                                                            ['Jan' ;  'Nov' ;  'Dec']
    ## 113                                                                   ['Jan' ;  'Feb' ;  'Nov' ;  'Dec']
    ## 114                                                                                             ['none']
    ## 115                                                                                     ['Jan' ;  'Dec']
    ## 116                                                                           ['Sept' ;  'Oct' ;  'Nov']
    ## 117                                                                           ['Sept' ;  'Oct' ;  'Nov']
    ## 118                                                                                              ['Nov']
    ## 119                                                                                             ['none']
    ## 120                                                                                     ['Feb' ;  'Mar']
    ## 121                                                                            ['Jan' ;  'Nov' ;  'Dec']
    ## 122                                                                            ['Jan' ;  'Feb' ;  'Dec']
    ## 123                                                                   ['Jan' ;  'Oct' ;  'Nov' ;  'Dec']
    ## 124                                                                                              ['Nov']
    ## 125                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 126                                                                            ['Jan' ;  'Nov' ;  'Dec']
    ## 127                                                                            ['Oct' ;  'Nov' ;  'Dec']
    ## 128                                                                                             ['none']
    ## 129                                                                           ['Sept' ;  'Oct' ;  'Nov']
    ## 130                                                                                     ['Nov' ;  'Dec']
    ## 131                                                                                     ['Oct' ;  'Nov']
    ##                                                                                                                                   no_food_mitigation
    ## 1                                                                                 ['na' ;  'rely_less_food' ;  'reduce_meals' ;  'day_night_hungry']
    ## 2                                                                ['na' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'seek_government']
    ## 3                                                                                                       ['na' ;  'restrict_adults' ;  'lab_ex_food']
    ## 4                                                                                     ['na' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 5                                                                                                                 ['na' ;  'go_forest' ;  'migrate']
    ## 6                                                                                              ['borrow_food' ;  'lab_ex_food' ;  'seek_government']
    ## 7                                                                                                                                    ['lab_ex_food']
    ## 8                                                      ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food']
    ## 9                                                     ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 10                                                                       ['rely_less_food' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 11                                                                                                               ['rely_less_food' ;  'lab_ex_food']
    ## 12                                                                          ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'lab_ex_food']
    ## 13                                                                                                                                   ['lab_ex_food']
    ## 14                                                                                                                 ['reduce_meals' ;  'lab_ex_food']
    ## 15                                                                  ['na' ;  'rely_less_food' ;  'limit_portion' ;  'reduce_meals' ;  'lab_ex_food']
    ## 16                                                                                                                                   ['lab_ex_food']
    ## 17                                                                                                                                   ['lab_ex_food']
    ## 18                                                                                                                 ['reduce_meals' ;  'lab_ex_food']
    ## 19                                                                       ['rely_less_food' ;  'limit_portion' ;  'lab_ex_food' ;  'seek_government']
    ## 20                                                                                                               ['rely_less_food' ;  'lab_ex_food']
    ## 21                                                                    ['rely_less_food' ;  'restrict_adults' ;  'day_night_hungry' ;  'lab_ex_food']
    ## 22                                                                              ['rely_less_food' ;  'reduce_meals' ;  'go_forest' ;  'lab_ex_food']
    ## 23                                                                                                                                            ['na']
    ## 24                                                                                                                                   ['lab_ex_food']
    ## 25                                                                                                                                            ['na']
    ## 26                                                                                                                                            ['na']
    ## 27                                                                                                                                            ['na']
    ## 28                                                             ['rely_less_food' ;  'reduce_meals' ;  'borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 29                                                                                                             ['rely_less_food' ;  'limit_variety']
    ## 30                                                    ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 31                                                                                                                                            ['na']
    ## 32                                                                                                                                            ['na']
    ## 33                                                                                                                                            ['na']
    ## 34                                                    ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'restrict_adults' ;  'lab_ex_food']
    ## 35                                    ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'restrict_adults' ;  'go_forest']
    ## 36                                                                                                                                            ['na']
    ## 37                                                                                            ['rely_less_food' ;  'limit_variety' ;  'lab_ex_food']
    ## 38                                                                                                                ['limit_variety' ;  'lab_ex_food']
    ## 39                                                                                                                                   ['lab_ex_food']
    ## 40                                                                                                                                   ['lab_ex_food']
    ## 41                                                                                                               ['limit_portion' ;  'reduce_meals']
    ## 42                                                                                           ['rely_less_food' ;  'limit_variety' ;  'reduce_meals']
    ## 43                                                                                                                                   ['lab_ex_food']
    ## 44                                                                                                                                   ['borrow_food']
    ## 45                                                                                                                                            ['na']
    ## 46                                                                                                                                   ['lab_ex_food']
    ## 47                                                                                                                                            ['na']
    ## 48                                                                                                                                 ['limit_variety']
    ## 49                                                                                                  ['reduce_meals' ;  'go_forest' ;  'lab_ex_food']
    ## 50                                                                                                   ['borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 51                                                                                                                    ['go_forest' ;  'lab_ex_food']
    ## 52                                                                                                               ['limit_variety' ;  'reduce_meals']
    ## 53                                                                                                             ['rely_less_food' ;  'limit_portion']
    ## 54                                                                                                               ['rely_less_food' ;  'lab_ex_food']
    ## 55                                                                                                                                   ['lab_ex_food']
    ## 56                                                                                                                                            ['na']
    ## 57                                                                                                                                            ['na']
    ## 58                                                                                                                                            ['na']
    ## 59                                                                                                                                            ['na']
    ## 60                                                                                                                                            ['na']
    ## 61                                                                      ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults']
    ## 62  ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 63                                                                      ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults']
    ## 64                                                     ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 65                                                                          ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'lab_ex_food']
    ## 66                                                                                                                                            ['na']
    ## 67                                                                                                                                            ['na']
    ## 68                                                                                                                                            ['na']
    ## 69                                                                                                                                            ['na']
    ## 70                                                                                                                                            ['na']
    ## 71                 ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'lab_ex_food']
    ## 72                                                                                                                  ['borrow_food' ;  'lab_ex_food']
    ## 73                                                                                                                                            ['na']
    ## 74                                                                                                                                            ['na']
    ## 75                                     ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'no_food' ;  'day_night_hungry']
    ## 76                                                              ['limit_variety' ;  'reduce_meals' ;  'borrow_food' ;  'go_forest' ;  'lab_ex_food']
    ## 77                                                                                                                                            ['na']
    ## 78                                                                                                                                            ['na']
    ## 79                                                                                             ['rely_less_food' ;  'reduce_meals' ;  'lab_ex_food']
    ## 80                                                                                                                                            ['na']
    ## 81                                                                                                                                            ['na']
    ## 82                                                                                                                                            ['na']
    ## 83                                                                                                                                            ['na']
    ## 84                                                                                                                                   ['lab_ex_food']
    ## 85                                                                                                                                            ['na']
    ## 86                                                                                           ['rely_less_food' ;  'limit_variety' ;  'reduce_meals']
    ## 87                                                                                                                 ['reduce_meals' ;  'lab_ex_food']
    ## 88                                                                                                                  ['borrow_food' ;  'lab_ex_food']
    ## 89                                                     ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 90                                                       ['rely_less_food' ;  'limit_variety' ;  'limit_portion' ;  'reduce_meals' ;  'lab_ex_food']
    ## 91                                                                                                             ['rely_less_food' ;  'limit_variety']
    ## 92                                                                                                                                            ['na']
    ## 93                                                                                                                  ['borrow_food' ;  'lab_ex_food']
    ## 94                                                                                                                                            ['na']
    ## 95                                                                             ['rely_less_food' ;  'limit_variety' ;  'go_forest' ;  'lab_ex_food']
    ## 96                                    ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'lab_ex_food']
    ## 97                                                                                                                                     ['go_forest']
    ## 98                                                                                                                                   ['lab_ex_food']
    ## 99                                                                                                                                            ['na']
    ## 100                                                                                                                                           ['na']
    ## 101                                                                                                                   ['go_forest' ;  'lab_ex_food']
    ## 102                                                                                                                                  ['lab_ex_food']
    ## 103                                                                                                             ['lab_ex_food' ;  'seek_government']
    ## 104                                                                                          ['rely_less_food' ;  'limit_portion' ;  'reduce_meals']
    ## 105                                                                                                                                           ['na']
    ## 106                                                                                                                                           ['na']
    ## 107                                                        ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'borrow_food' ;  'lab_ex_food']
    ## 108                                                                                                                 ['borrow_food' ;  'lab_ex_food']
    ## 109                                                                                                                                           ['na']
    ## 110                                                                                                                                           ['na']
    ## 111                                                                                          ['rely_less_food' ;  'limit_portion' ;  'reduce_meals']
    ## 112                                                                         ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'lab_ex_food']
    ## 113                                   ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'borrow_food' ;  'lab_ex_food']
    ## 114                                                                                                                                           ['na']
    ## 115                                                                                                            ['rely_less_food' ;  'limit_variety']
    ## 116                                                                                                                ['reduce_meals' ;  'lab_ex_food']
    ## 117                                                                                                                                  ['lab_ex_food']
    ## 118                                                                                                                                  ['lab_ex_food']
    ## 119                                                                                                                                           ['na']
    ## 120                                                                                                                   ['go_forest' ;  'lab_ex_food']
    ## 121                                                                                                                                  ['lab_ex_food']
    ## 122                                                                                                                                  ['lab_ex_food']
    ## 123                                                                                                                                           ['na']
    ## 124                                                                                                                                           ['na']
    ## 125                                                                                                                   ['go_forest' ;  'lab_ex_food']
    ## 126                                                                                                                                  ['borrow_food']
    ## 127                                                                                                              ['rely_less_food' ;  'lab_ex_food']
    ## 128                                                                                                                                           ['na']
    ## 129                                                                                                                                  ['lab_ex_food']
    ## 130                                                    ['rely_less_food' ;  'limit_variety' ;  'reduce_meals' ;  'restrict_adults' ;  'lab_ex_food']
    ## 131                                                                                         ['rely_less_food' ;  'restrict_adults' ;  'borrow_food']
    ##      Latitude Longitude Altitude Accuracy
    ## 1   -19.11226  33.48346      698   14.000
    ## 2   -19.11248  33.48342      690   19.000
    ## 3   -19.11211  33.48345      674   13.000
    ## 4   -19.11223  33.48342      679    5.000
    ## 5   -19.11222  33.48343      689   10.000
    ## 6   -19.11220  33.48339      692   12.000
    ## 7   -19.11222  33.48336      709   11.000
    ## 8   -19.11216  33.48342      700    9.000
    ## 9   -19.11222  33.48344      701   11.000
    ## 10  -19.11221  33.48339      710   14.000
    ## 11  -19.11219  33.48346      707   10.000
    ## 12  -19.11229  33.48342      696   13.000
    ## 13  -19.11237  33.48356      706   15.000
    ## 14  -19.11222  33.48344      698   11.000
    ## 15  -19.11208  33.48340      715    9.000
    ## 16  -19.11211  33.48344      709    9.000
    ## 17  -19.11218  33.48346      710   10.000
    ## 18  -19.11134  33.47631      685   17.000
    ## 19  -19.11143  33.47641      716   30.000
    ## 20  -19.11147  33.47619      700   27.000
    ## 21  -19.11155  33.47623      707   20.000
    ## 22  -19.11213  33.48351      722    9.000
    ## 23  -19.11219  33.48338      699   10.000
    ## 24  -19.11219  33.48343      745   11.000
    ## 25  -19.11223  33.48348      698   11.000
    ## 26  -19.11230  33.48354      706   12.000
    ## 27  -19.04300  33.40508      679   14.000
    ## 28  -19.04291  33.40507      721    7.000
    ## 29  -19.04302  33.40507      657    6.000
    ## 30  -19.04300  33.40505      669    5.000
    ## 31  -19.04302  33.40509      704    4.000
    ## 32  -19.04411  33.40391      703    8.000
    ## 33  -19.04415  33.40384      695    5.000
    ## 34  -19.11219  33.48342      706   11.000
    ## 35  -19.11211  33.48343      733   11.000
    ## 36  -19.11218  33.48338      710   10.000
    ## 37  -19.11218  33.48340      711   12.000
    ## 38  -19.11223  33.48337      696    9.000
    ## 39  -19.04336  33.40467        0   20.000
    ## 40  -19.04336  33.40467        0   22.112
    ## 41  -19.04339  33.40485      679   13.000
    ## 42  -19.04346  33.40485      699   10.000
    ## 43  -19.04303  33.40473      605   30.000
    ## 44  -19.04315  33.40458      716   11.000
    ## 45  -19.04312  33.40466      703   28.000
    ## 46  -19.04307  33.40458      703    5.000
    ## 47  -19.11226  33.48340      689    5.000
    ## 48  -19.11223  33.48353      689   12.000
    ## 49  -19.11228  33.48335      694   12.000
    ## 50  -19.11220  33.48345      718   12.000
    ## 51  -19.11221  33.48338      709   12.000
    ## 52  -19.11224  33.48335      694   10.000
    ## 53  -19.11217  33.48344      687   10.000
    ## 54  -19.11220  33.48336      681    9.000
    ## 55  -19.11229  33.48333      702   11.000
    ## 56  -19.11217  33.48342      689   10.000
    ## 57  -19.11228  33.48339      695   10.000
    ## 58  -19.11218  33.48332      723   11.000
    ## 59  -19.11234  33.48333      683   13.000
    ## 60  -19.11226  33.48341      694   11.000
    ## 61  -19.11218  33.48342      712   13.000
    ## 62  -19.11217  33.48340      719   18.000
    ## 63  -19.11220  33.48339      702   25.000
    ## 64  -19.11220  33.48340      704    9.000
    ## 65  -19.11221  33.48341      706   39.000
    ## 66  -19.11217  33.48339      702    8.000
    ## 67  -19.11209  33.48339      717   11.000
    ## 68  -19.11215  33.48348      710   10.000
    ## 69  -19.11217  33.48340      708    8.000
    ## 70  -19.11217  33.48341      707    8.000
    ## 71  -19.11221  33.48333      696    4.000
    ## 72  -19.11221  33.48341      676    8.000
    ## 73  -19.10413  33.47776        0 2099.999
    ## 74  -19.11210  33.48345      702   11.000
    ## 75  -19.11224  33.48345      691   12.000
    ## 76  -19.11221  33.48342      713   13.000
    ## 77  -19.11236  33.48356      714   50.000
    ## 78  -19.11205  33.48349      713    9.000
    ## 79  -19.11205  33.48347      701    4.000
    ## 80  -19.11208  33.48351      701    5.000
    ## 81  -19.11204  33.48345      694    4.000
    ## 82  -19.11232  33.48346      690   10.000
    ## 83  -19.11223  33.48349      691   13.000
    ## 84  -19.11221  33.48342      706    9.000
    ## 85  -19.11220  33.48340      694   10.000
    ## 86  -19.11219  33.48338      714   11.000
    ## 87  -19.11212  33.48339      716    7.000
    ## 88  -19.11217  33.48339      685   10.000
    ## 89  -19.11219  33.48340      705    5.000
    ## 90  -19.11221  33.48347      716    5.000
    ## 91  -19.11220  33.48341      714    4.000
    ## 92  -19.11220  33.48342      702    9.000
    ## 93  -19.11232  33.48350      693   33.000
    ## 94  -19.11235  33.48359      697   10.000
    ## 95  -19.11232  33.48348      710   13.000
    ## 96  -19.11224  33.48342      702   11.000
    ## 97  -19.11219  33.48337      712    9.000
    ## 98  -19.04413  33.40389      691   11.000
    ## 99  -19.04403  33.40398      723   11.000
    ## 100 -19.04415  33.40390      689    6.000
    ## 101 -19.11226  33.48337      711    9.000
    ## 102 -19.11221  33.48351      735   11.000
    ## 103 -19.11221  33.48341      709    5.000
    ## 104 -19.11222  33.48338      699   10.000
    ## 105 -19.11220  33.48340      704    9.000
    ## 106 -19.11223  33.48341      706   12.000
    ## 107 -19.11221  33.48344      713    9.000
    ## 108 -19.11218  33.48341      682   11.000
    ## 109 -19.11226  33.48335      706    5.000
    ## 110 -19.11147  33.47610        0   20.000
    ## 111 -19.11147  33.47610        0   20.000
    ## 112 -19.11147  33.47610        0   20.000
    ## 113 -19.11147  33.47610        0   20.000
    ## 114 -19.11219  33.48342      710    5.000
    ## 115 -19.11248  33.47633        0 1911.000
    ## 116 -19.11148  33.47618      709   17.000
    ## 117 -19.11149  33.47618      712   28.000
    ## 118 -19.11218  33.48345      711   12.000
    ## 119 -19.11217  33.48347      708    9.000
    ## 120 -19.11386  33.48267        0 1799.999
    ## 121 -19.11499  33.48827        0 2000.000
    ## 122 -19.11217  33.48341      703    3.000
    ## 123 -19.11218  33.48336      705    5.000
    ## 124 -19.11217  33.48342      714    4.000
    ## 125 -19.11219  33.48338      709    9.000
    ## 126 -19.11215  33.48336      705    4.000
    ## 127 -19.11219  33.48338      700    7.000
    ## 128 -19.11216  33.48339      720    9.000
    ## 129 -19.11227  33.48347      719   10.000
    ## 130 -19.11228  33.48339      711    5.000
    ## 131 -19.11218  33.48337      681   20.000
    ##                                        anceID         start_clean
    ## 1   uuid:ec241f2c-0609-46ed-b5e8-fe575f6cefef 2017-03-23 09:49:57
    ## 2   uuid:099de9c9-3e5e-427b-8452-26250e840d6e 2017-04-02 09:48:16
    ## 3   uuid:193d7daf-9582-409b-bf09-027dd36f9007 2017-04-02 14:35:26
    ## 4   uuid:148d1105-778a-4755-aa71-281eadd4a973 2017-04-02 14:55:18
    ## 5   uuid:2c867811-9696-4966-9866-f35c3e97d02d 2017-04-02 15:10:35
    ## 6   uuid:daa56c91-c8e3-44c3-a663-af6a49a2ca70 2017-04-02 15:27:25
    ## 7   uuid:ae20a58d-56f4-43d7-bafa-e7963d850844 2017-04-02 15:38:01
    ## 8   uuid:d6cee930-7be1-4fd9-88c0-82a08f90fb5a 2017-04-02 15:59:52
    ## 9   uuid:846103d2-b1db-4055-b502-9cd510bb7b37 2017-04-02 16:23:36
    ## 10  uuid:8f4e49bc-da81-4356-ae34-e0d794a23721 2017-04-02 17:03:28
    ## 11  uuid:d29b44e3-3348-4afc-aa4d-9eb34c89d483 2017-04-03 03:16:15
    ## 12  uuid:e6ee6269-b467-4e37-91fc-5e9eaf934557 2017-04-03 03:31:13
    ## 13  uuid:6c00c145-ee3b-409c-8c02-2c8d743b6918 2017-04-03 03:58:43
    ## 14  uuid:9b21467f-1116-4340-a3b1-1ab64f13c87d 2017-04-03 04:19:57
    ## 15  uuid:a837e545-ff86-4a1c-a1a5-6186804b985f 2017-04-03 05:12:17
    ## 16  uuid:d17db52f-4b87-4768-b534-ea8f9704c565 2017-04-03 05:29:24
    ## 17  uuid:4707f3dc-df18-4348-9c2c-eec651e89b6b 2017-04-03 05:41:42
    ## 18  uuid:7ffe7bd1-a15c-420c-a137-e1f006c317a3 2017-04-03 12:27:04
    ## 19  uuid:e32f2dc0-0d05-42fb-8e21-605757ddf07d 2017-04-03 12:40:14
    ## 20  uuid:d1005274-bf52-4e79-8380-3350dd7c2bac 2017-04-03 14:04:50
    ## 21  uuid:6570a7d0-6a0b-452c-aa2e-922500e35749 2017-04-03 14:24:58
    ## 22  uuid:a51c3006-8847-46ff-9d4e-d29919b8ecf9 2017-04-03 16:28:52
    ## 23  uuid:58b37b6d-d6cd-4414-8790-b9c68bca98de 2017-04-03 16:41:04
    ## 24  uuid:661457d3-7e61-45e8-a238-7415e7548f82 2017-04-03 17:19:49
    ## 25  uuid:45ed84c4-114e-4df0-9f5d-c800806c2bee 2017-04-04 04:01:58
    ## 26  uuid:1c54ee24-22c4-4ee9-b1ad-42d483c08e2e 2017-04-04 04:30:19
    ## 27  uuid:3197cded-1fdc-4c0c-9b10-cfcc0bf49c4d 2017-04-05 04:59:42
    ## 28  uuid:1de53318-a8cf-4736-99b1-8239f8822473 2017-04-05 05:14:49
    ## 29  uuid:adcd7463-8943-4c67-b25f-f72311409476 2017-04-05 05:37:30
    ## 30  uuid:59341ead-92be-45a9-8545-6edf9f94fdc6 2017-04-05 06:05:58
    ## 31  uuid:cb06eb49-dd39-4150-8bbe-a599e074afe8 2017-04-05 06:21:20
    ## 32  uuid:25597af3-cd79-449c-a48a-fb9aea6c48bf 2017-04-05 06:38:55
    ## 33  uuid:0fbd2df1-2640-4550-9fbd-7317feaa4758 2017-04-05 08:08:19
    ## 34  uuid:14c78c45-a7cc-4b2a-b765-17c82b43feb4 2017-04-05 16:00:47
    ## 35  uuid:ff7496e7-984a-47d3-a8a1-13618b5683ce 2017-04-05 16:22:13
    ## 36  uuid:c90eade0-1148-4a12-8c0e-6387a36f45b1 2017-04-05 16:50:48
    ## 37  uuid:408c6c93-d723-45ef-8dee-1b1bd3fe20cd 2017-04-05 17:17:48
    ## 38  uuid:81309594-ff58-4dc1-83a7-72af5952ee08 2017-04-05 17:28:12
    ## 39  uuid:c0fb6310-55af-4831-ae3d-2729556c3285 2017-04-06 08:31:17
    ## 40  uuid:c0b34854-eede-4e81-b183-ef58a45bfc34 2017-04-06 08:44:51
    ## 41  uuid:b3ba34d8-eea1-453d-bc73-c141bcbbc5e5 2017-04-06 09:03:50
    ## 42  uuid:e3a1dd8a-1bda-428c-a014-2b527f11ae64 2017-04-06 09:14:22
    ## 43  uuid:b4dff49f-ef27-40e5-a9d1-acf287b47358 2017-04-06 09:31:56
    ## 44  uuid:f9fadf44-d040-4fca-86c1-2835f79c4952 2017-04-06 14:44:32
    ## 45  uuid:e3554d22-35b1-4fb9-b386-dd5866ad5792 2017-04-06 14:53:04
    ## 46  uuid:35f297e0-aa5d-4149-9b7b-4965004cfc37 2017-04-06 15:19:41
    ## 47  uuid:2d0b1936-4f82-4ec3-a3b5-7c3c8cd6cc2b 2017-04-07 14:05:25
    ## 48  uuid:e180899c-7614-49eb-a97c-40ed013a38a2 2017-04-07 14:19:49
    ## 49  uuid:2303ebc1-2b3c-475a-8916-b322ebf18440 2017-04-07 14:43:09
    ## 50  uuid:4267c33c-53a7-46d9-8bd6-b96f58a4f92c 2017-04-07 14:56:01
    ## 51  uuid:18ac8e77-bdaf-47ab-85a2-e4c947c9d3ce 2017-04-07 15:27:45
    ## 52  uuid:6db55cb4-a853-4000-9555-757b7fae2bcf 2017-04-08 04:44:09
    ## 53  uuid:cc7f75c5-d13e-43f3-97e5-4f4c03cb4b12 2017-04-08 05:03:08
    ## 54  uuid:273ab27f-9be3-4f3b-83c9-d3e1592de919 2017-04-08 05:36:55
    ## 55  uuid:883c0433-9891-4121-bc63-744f082c1fa0 2017-04-08 05:52:32
    ## 56  uuid:973c4ac6-f887-48e7-aeaf-4476f2cfab76 2017-04-08 06:05:59
    ## 57  uuid:a7184e55-0615-492d-9835-8f44f3b03a71 2017-04-08 06:26:22
    ## 58  uuid:a7a3451f-cd0d-4027-82d9-8dcd1234fcca 2017-04-08 08:25:49
    ## 59  uuid:1936db62-5732-45dc-98ff-9b3ac7a22518 2017-04-08 08:52:05
    ## 60  uuid:85465caf-23e4-4283-bb72-a0ef30e30176 2017-04-08 09:03:01
    ## 61  uuid:2401cf50-8859-44d9-bd14-1bf9128766f2 2017-04-08 10:47:11
    ## 62  uuid:c6597ecc-cc2a-4c35-a6dc-e62c71b345d6 2017-04-08 13:27:58
    ## 63  uuid:86ed4328-7688-462f-aac7-d6518414526a 2017-04-08 13:41:39
    ## 64  uuid:28cfd718-bf62-4d90-8100-55fafbe45d06 2017-04-08 13:52:30
    ## 65  uuid:143f7478-0126-4fbc-86e0-5d324339206b 2017-04-08 14:02:49
    ## 66  uuid:a457eab8-971b-4417-a971-2e55b8702816 2017-04-08 21:09:38
    ## 67  uuid:6c15d667-2860-47e3-a5e7-7f679271e419 2017-04-08 21:34:23
    ## 68  uuid:ef04b3eb-b47d-412e-9b09-4f5e08fc66f9 2017-04-08 21:49:40
    ## 69  uuid:f86933a5-12b8-4427-b821-43c5b039401d 2017-04-09 22:08:07
    ## 70  uuid:1feb0108-4599-4bf9-8a07-1f5e66a50a0a 2017-04-09 22:21:23
    ## 71  uuid:761f9c49-ec93-4932-ba4c-cc7b78dfcef1 2017-04-09 15:00:19
    ## 72  uuid:f6d04b41-b539-4e00-868a-0f62b427587d 2017-04-09 05:16:06
    ## 73  uuid:429d279a-a519-4dcc-9f64-4673b0fd5d53 2017-04-09 05:27:46
    ## 74  uuid:59738c17-1cda-49ee-a563-acd76f6bc487 2017-04-09 05:47:31
    ## 75  uuid:7e7961ca-fa1c-4567-9bfa-a02f876e4e03 2017-04-09 06:16:49
    ## 76  uuid:77b3021b-a9d6-4276-aaeb-5bfcfd413852 2017-04-09 06:35:16
    ## 77  uuid:2186e2ec-f65a-47cc-9bc1-a0f36dd9591c 2017-04-09 06:54:49
    ## 78  uuid:87998c33-c8d2-49ec-9dae-c123735957ec 2017-04-09 07:59:49
    ## 79  uuid:ece89122-ea99-4378-b67e-a170127ec4e6 2017-04-09 08:23:05
    ## 80  uuid:bf373763-dca5-4906-901b-d1bacb4f0286 2017-04-09 08:43:08
    ## 81  uuid:394033e8-a6e2-4e39-bfac-458753a1ed78 2017-04-09 09:08:04
    ## 82  uuid:268bfd97-991c-473f-bd51-bc80676c65c6 2017-04-09 15:20:26
    ## 83  uuid:0a42c9ee-a840-4dda-8123-15c1bede5dfc 2017-04-09 15:48:14
    ## 84  uuid:2c132929-9c8f-450a-81ff-367360ce2c19 2017-04-09 16:13:19
    ## 85  uuid:44e427d1-a448-4bf2-b529-7d67b2266c06 2017-04-09 18:00:41
    ## 86  uuid:85c99fd2-775f-40c9-8654-68223f59d091 2017-04-09 18:32:09
    ## 87  uuid:28c64954-739c-444c-a6e0-355878e471c8 2017-04-09 19:15:21
    ## 88  uuid:9e79a31c-3ea5-44f0-80f9-a32db49422e3 2017-04-09 19:31:47
    ## 89  uuid:06d39051-38ef-4757-b68b-3327b1f16b9d 2017-04-09 19:48:09
    ## 90  uuid:c4a2c982-244e-45a5-aa4b-71fa53f99e18 2017-04-26 15:46:24
    ## 91  uuid:ac3da862-9e6c-4962-94b6-f4c31624f207 2017-04-26 16:13:50
    ## 92  uuid:4178a296-903a-4a8e-9cfa-0cd6143476e8 2017-04-26 16:45:28
    ## 93  uuid:a1e9df00-c8ae-411c-931c-c7df898c68d0 2017-04-27 12:27:31
    ## 94  uuid:4d0f472b-f8ae-4026-87c9-6b5be14b0a70 2017-04-27 12:58:02
    ## 95  uuid:b3b309c6-f234-4830-8b30-87d26a17ee1d 2017-04-27 16:11:23
    ## 96  uuid:3c174acd-e431-4523-9ad6-eb14cddca805 2017-04-27 16:42:02
    ## 97  uuid:e9d79844-ef14-493b-bbd6-d13691cc660e 2017-04-27 17:38:53
    ## 98  uuid:76206b0b-af74-4344-b24f-81e839f0d7b0 2017-04-28 06:27:07
    ## 99  uuid:da3fa7cc-5ce9-44fd-9a78-b8982b607515 2017-04-28 07:09:39
    ## 100 uuid:a85df6df-0336-46fa-a9f4-522bf6f8b438 2017-04-28 09:01:47
    ## 101 uuid:bb2bb365-7d7d-4fe9-9353-b21269676119 2017-04-28 14:25:13
    ## 102 uuid:af0904ee-4fdb-4090-973f-599c81ddf022 2017-04-28 15:32:38
    ## 103 uuid:468797c1-4a65-4f35-9c83-e28ce46972a2 2017-04-30 05:51:18
    ## 104 uuid:602cd3f6-4a97-49c6-80e3-bcfd5c78dfa4 2017-05-03 13:14:43
    ## 105 uuid:e7c51ac4-24e4-475e-88e7-f85e896945e3 2017-05-03 13:37:57
    ## 106 uuid:01210861-aba1-4268-98d0-0260e05f5155 2017-05-03 14:00:13
    ## 107 uuid:77335b2e-8812-4a35-b1e5-ca9ab626dfea 2017-05-04 10:26:35
    ## 108 uuid:02b05c68-302e-4e7a-b229-81cb1377fd29 2017-05-04 10:47:05
    ## 109 uuid:fa201fce-4e94-44b8-b435-c558c2e1ed55 2017-05-04 11:16:57
    ## 110 uuid:628fe23d-188f-43e4-a203-a4bf3257d461 2017-05-11 05:24:25
    ## 111 uuid:e4f4d6ba-e698-45a5-947f-ba6da88cc22b 2017-05-11 05:42:08
    ## 112 uuid:cfee6297-2c0e-4f8a-94cc-9aaee0bd64cb 2017-05-11 06:09:56
    ## 113 uuid:3fe626b3-c794-48e1-a80f-5bfe440c507b 2017-05-11 06:28:02
    ## 114 uuid:0670cef6-d233-4852-89d8-36955261b0a3 2017-05-18 04:36:23
    ## 115 uuid:9a096a12-b335-468c-b3cc-1191180d62de 2017-05-18 05:55:04
    ## 116 uuid:92613d0d-e7b1-4d62-8ea4-451d7cd0a982 2017-05-18 10:37:37
    ## 117 uuid:37577f91-d665-443e-8d70-b914954cef4b 2017-05-18 10:56:16
    ## 118 uuid:f22831ec-6bc3-4b73-9197-4b01e01abb66 2017-06-03 05:08:49
    ## 119 uuid:62f3f7af-f0f3-4f88-b9e0-acf8baa49ae4 2017-06-03 05:32:33
    ## 120 uuid:40aac732-94df-496c-97ba-5b67f59bcc7a 2017-06-03 05:53:28
    ## 121 uuid:a9d1a013-043b-475d-a71b-77ed80abe970 2017-06-03 06:25:09
    ## 122 uuid:43ec6132-478c-4f87-878d-fb3c0c4d0c74 2017-06-03 06:50:47
    ## 123 uuid:64fc743e-8176-40f6-8ae4-36ae97fac1d9 2017-06-03 07:21:48
    ## 124 uuid:c17e374c-280b-4e78-bf21-74a7c1c73492 2017-06-03 15:23:01
    ## 125 uuid:dad53aff-b520-4015-a9e3-f5fdf9168fe1 2017-06-03 15:54:03
    ## 126 uuid:f94409a6-e461-4e4c-a6fb-0072d3d58b00 2017-06-03 16:17:55
    ## 127 uuid:69caea81-a4e5-4e8d-83cd-9c18d8e8d965 2017-05-18 04:13:37
    ## 128 uuid:5ccc2e5a-ea90-48b5-8542-69400d5334df 2017-06-04 09:36:20
    ## 129 uuid:95c11a30-d44f-40c4-8ea8-ec34fca6bbbf 2017-06-04 10:13:36
    ## 130 uuid:ffc83162-ff24-4a87-8709-eff17abc0b3b 2017-06-04 10:33:55
    ## 131 uuid:aa77a0d7-7142-41c8-b494-483a5b68d8a7 2017-06-04 10:52:46
    ##               end_clean
    ## 1   2017-04-02 17:29:08
    ## 2   2017-04-02 17:26:19
    ## 3   2017-04-02 17:26:53
    ## 4   2017-04-02 17:27:16
    ## 5   2017-04-02 17:27:35
    ## 6   2017-04-02 17:28:02
    ## 7   2017-04-02 17:28:19
    ## 8   2017-04-02 17:28:39
    ## 9   2017-04-02 16:42:08
    ## 10  2017-04-02 17:25:11
    ## 11  2017-04-03 03:31:10
    ## 12  2017-04-03 03:58:34
    ## 13  2017-04-03 04:19:36
    ## 14  2017-04-03 04:50:05
    ## 15  2017-04-03 05:28:44
    ## 16  2017-04-03 05:40:53
    ## 17  2017-04-03 05:57:57
    ## 18  2017-04-03 12:39:48
    ## 19  2017-04-03 12:53:29
    ## 20  2017-04-03 14:20:04
    ## 21  2017-04-03 14:44:39
    ## 22  2017-04-03 16:40:47
    ## 23  2017-04-03 17:04:28
    ## 24  2017-04-03 17:43:01
    ## 25  2017-04-04 04:29:47
    ## 26  2017-04-04 04:44:19
    ## 27  2017-04-05 05:14:45
    ## 28  2017-04-05 05:36:18
    ## 29  2017-04-05 06:05:44
    ## 30  2017-04-05 06:20:39
    ## 31  2017-04-05 06:38:26
    ## 32  2017-04-05 08:05:32
    ## 33  2017-04-05 08:25:48
    ## 34  2017-04-05 16:21:59
    ## 35  2017-04-05 16:50:25
    ## 36  2017-04-05 17:10:53
    ## 37  2017-04-05 17:26:51
    ## 38  2017-04-05 17:50:57
    ## 39  2017-04-06 08:44:47
    ## 40  2017-04-06 09:03:47
    ## 41  2017-04-06 09:14:05
    ## 42  2017-04-06 09:30:54
    ## 43  2017-04-06 09:53:53
    ## 44  2017-04-06 14:53:01
    ## 45  2017-04-06 15:11:57
    ## 46  2017-04-06 15:45:32
    ## 47  2017-04-07 14:19:45
    ## 48  2017-04-07 14:40:23
    ## 49  2017-04-07 14:55:51
    ## 50  2017-04-07 15:26:23
    ## 51  2017-04-07 15:39:10
    ## 52  2017-04-08 05:02:58
    ## 53  2017-04-08 05:33:51
    ## 54  2017-04-08 05:52:15
    ## 55  2017-04-08 06:05:41
    ## 56  2017-04-08 06:26:12
    ## 57  2017-04-08 06:39:40
    ## 58  2017-04-08 08:48:51
    ## 59  2017-04-08 09:02:34
    ## 60  2017-04-08 09:20:18
    ## 61  2017-04-08 11:14:09
    ## 62  2017-04-08 13:41:21
    ## 63  2017-04-08 13:52:07
    ## 64  2017-04-08 14:02:24
    ## 65  2017-04-08 14:15:45
    ## 66  2017-04-08 21:33:45
    ## 67  2017-04-08 21:49:02
    ## 68  2017-04-09 22:06:57
    ## 69  2017-04-09 22:21:08
    ## 70  2017-04-09 22:40:57
    ## 71  2017-04-09 15:19:22
    ## 72  2017-04-09 05:27:41
    ## 73  2017-04-09 05:43:51
    ## 74  2017-04-09 06:16:11
    ## 75  2017-04-09 06:28:48
    ## 76  2017-04-09 06:48:01
    ## 77  2017-04-09 07:14:16
    ## 78  2017-04-09 08:22:34
    ## 79  2017-04-09 08:42:02
    ## 80  2017-04-09 09:07:48
    ## 81  2017-04-09 09:34:12
    ## 82  2017-04-09 15:46:14
    ## 83  2017-04-09 16:12:46
    ## 84  2017-04-09 16:35:24
    ## 85  2017-04-09 18:31:40
    ## 86  2017-04-09 19:14:52
    ## 87  2017-04-09 19:27:56
    ## 88  2017-04-09 19:45:38
    ## 89  2017-04-09 20:08:15
    ## 90  2017-04-26 16:13:33
    ## 91  2017-04-26 16:45:01
    ## 92  2017-04-26 17:26:21
    ## 93  2017-04-27 12:56:42
    ## 94  2017-04-27 13:23:06
    ## 95  2017-04-27 16:41:41
    ## 96  2017-04-27 18:11:54
    ## 97  2017-04-27 18:09:45
    ## 98  2017-04-28 06:52:04
    ## 99  2017-04-28 07:31:38
    ## 100 2017-04-28 09:25:51
    ## 101 2017-04-28 15:18:10
    ## 102 2017-04-28 15:58:10
    ## 103 2017-04-30 06:47:01
    ## 104 2017-05-03 13:37:53
    ## 105 2017-05-03 13:58:06
    ## 106 2017-05-03 14:27:03
    ## 107 2017-05-04 10:46:35
    ## 108 2017-05-04 11:16:05
    ## 109 2017-05-04 11:38:38
    ## 110 2017-05-11 05:41:56
    ## 111 2017-05-11 06:08:58
    ## 112 2017-05-11 06:22:19
    ## 113 2017-05-11 06:55:35
    ## 114 2017-05-18 05:02:38
    ## 115 2017-05-18 06:37:10
    ## 116 2017-05-18 10:56:00
    ## 117 2017-05-18 11:07:35
    ## 118 2017-06-03 05:32:19
    ## 119 2017-06-03 05:51:49
    ## 120 2017-06-03 06:25:06
    ## 121 2017-06-03 06:45:06
    ## 122 2017-06-03 07:20:21
    ## 123 2017-06-03 07:51:29
    ## 124 2017-06-03 15:53:10
    ## 125 2017-06-03 16:17:26
    ## 126 2017-06-03 17:16:39
    ## 127 2017-05-18 04:35:47
    ## 128 2017-06-04 10:13:32
    ## 129 2017-06-04 10:32:06
    ## 130 2017-06-04 10:52:22
    ## 131 2017-06-04 11:08:13

## Regular Expressions

There are 2 questions using regular expressions below and each have two
parts. Choose **1** of the questions to answer. You must complete both
parts of whichever question you choose.

*Option 1*: Use str\_subset to find all the words in `stringr::words`
that are exactly 5 letters long.

1.  Using regular expressions

2.  Using rverbalexpressions

*Option 2*: Evaluate the rule “i before e except after c”. Are there any
exceptions to this in the `stringr::words` data? An exception would be
words where ie come after c, and words where ei occurs but it comes
after a letter other than c.

1.  Using regular expressions

``` r
stringr::words[str_detect(stringr::words, "cie")]
```

    ## [1] "science" "society"

``` r
stringr::words[str_detect(stringr::words,"[^c]ei")]
```

    ## [1] "weigh"

2.  Using rverbal expressions

``` r
x1 <- rx_find(value = "cie")
stringr::words[str_detect(stringr::words,x1)]
```

    ## [1] "science" "society"

``` r
x2 <- rx_something_but(value = "c") %>% 
  rx_find(value = "ei")
stringr::words[str_detect(stringr::words,x2)]
```

    ## [1] "weigh"

## Application of Regular Expressions

The dataframe population contains the world’s most populous cities. The
`Location` column indicates the location of the city in the format
“City, Country”. `UN.2018.Population.Estimate` is the population of the
city. `Population.per.Sq.km` indicates the population and area in
*k**m*<sup>2</sup> in the format population-area for the “city proper.”

[Source:](https://en.wikipedia.org/wiki/List_of_largest_cities#cite_note-UNpopulation-13)

``` r
(population <- read.csv("world_cities_population.csv"))
```

    ##                           Location UN.2018.population.estimates
    ## 1                     Tokyo, Japan                     37400068
    ## 2                     Delhi, India                     28514000
    ## 3                  Shanghai, China                     25582000
    ## 4                São Paulo, Brazil                     21650000
    ## 5              Mexico City, Mexico                     21581000
    ## 6                     Cairo, Egypt                     20076000
    ## 7                    Mumbai, India                     19980000
    ## 8                   Beijing, China                     19618000
    ## 9                Dhaka, Bangladesh                     19578000
    ## 10                    Osaka, Japan                     19281000
    ## 11    New York City, United States                     18819000
    ## 12               Karachi, Pakistan                     15400000
    ## 13         Buenos Aires, Argentina                     14967000
    ## 14                Chongqing, China                     14838000
    ## 15                Istanbul, Turkey                     14751000
    ## 16                  Kolkata, India                     14681000
    ## 17             Manila, Philippines                     13482000
    ## 18                  Lagos, Nigeria                     13463000
    ## 19          Rio de Janeiro, Brazil                     13293000
    ## 20                  Tianjin, China                     13215000
    ## 21              Kinshasa, DR Congo                     13171000
    ## 22                Guangzhou, China                     12638000
    ## 23      Los Angeles, United States                     12458000
    ## 24                  Moscow, Russia                     12410000
    ## 25                 Shenzhen, China                     11908000
    ## 26                Lahore, Pakistan                     11738000
    ## 27                Bangalore, India                     11440000
    ## 28                   Paris, France                     10901000
    ## 29                Bogotá, Colombia                     10574000
    ## 30              Jakarta, Indonesia                     10517000
    ## 31                  Chennai, India                     10456000
    ## 32                      Lima, Peru                     10391000
    ## 33               Bangkok, Thailand                     10156000
    ## 34              Seoul, South Korea                      9963000
    ## 35                   Nagoya, Japan                      9507000
    ## 36                Hyderabad, India                      9482000
    ## 37          London, United Kingdom                      9046000
    ## 38                    Tehran, Iran                      8896000
    ## 39          Chicago, United States                      8864000
    ## 40                  Chengdu, China                      8813000
    ## 41                  Nanjing, China                      8245000
    ## 42                    Wuhan, China                      8176000
    ## 43       Ho Chi Minh City, Vietnam                      8145000
    ## 44                  Luanda, Angola                      7774000
    ## 45                Ahmedabad, India                      7681000
    ## 46          Kuala Lumpur, Malaysia                      7564000
    ## 47                    Xi'an, China                      7444000
    ## 48                Hong Kong, China                      7429000
    ## 49                 Dongguan, China                      7360000
    ## 50                 Hangzhou, China                      7236000
    ## 51                   Foshan, China                      7236000
    ## 52                 Shenyang, China                      6921000
    ## 53            Riyadh, Saudi Arabia                      6907000
    ## 54                   Baghdad, Iraq                      6812000
    ## 55                 Santiago, Chile                      6680000
    ## 56                    Surat, India                      6564000
    ## 57                   Madrid, Spain                      6497000
    ## 58                   Suzhou, China                      6339000
    ## 59                     Pune, India                      6276000
    ## 60                   Harbin, China                      6115000
    ## 61          Houston, United States                      6115000
    ## 62           Dallas, United States                      6099000
    ## 63                 Toronto, Canada                      6082000
    ## 64         Dar es Salaam, Tanzania                      6048000
    ## 65            Miami, United States                      6036000
    ## 66          Belo Horizonte, Brazil                      5972000
    ## 67            Singapore, Singapore                      5792000
    ## 68     Philadelphia, United States                      5695000
    ## 69          Atlanta, United States                      5572000
    ## 70                  Fukuoka, Japan                      5551000
    ## 71                 Khartoum, Sudan                      5534000
    ## 72                Barcelona, Spain                      5494000
    ## 73      Johannesburg, South Africa                      5486000
    ## 74        Saint Petersburg, Russia                      5383000
    ## 75                  Qingdao, China                      5381000
    ## 76                   Dalian, China                      5300000
    ## 77 Washington, D.C., United States                      5207000
    ## 78                 Yangon, Myanmar                      5157000
    ## 79               Alexandria, Egypt                      5086000
    ## 80                    Jinan, China                      5052000
    ## 81             Guadalajara, Mexico                      5023000
    ##           City.Proper.Definition Population.per.Sq.km
    ## 1          Metropolis prefecture        13515271/2191
    ## 2     National capital territory        16753235/1484
    ## 3                   Municipality        24183000/6341
    ## 4                   Municipality        12252023/1521
    ## 5                     City-state         8918653/1485
    ## 6              Urban governorate         9500000/3085
    ## 7                   Municipality         12478447/603
    ## 8                   Municipality       21707000/16411
    ## 9                   Capital city          8906039/338
    ## 10               Designated city          2725006/225
    ## 11                          City          8398748/786
    ## 12             Metropolitan city        14910352/3530
    ## 13               Autonomous city          3054300/203
    ## 14                  Municipality       30165500/82403
    ## 15     Metropolitan municipality        15029231/5196
    ## 16                  Municipality          4496694/205
    ## 17                  Capital city           1780148/43
    ## 18                          <NA>                 <NA>
    ## 19                  Municipality         6520000/1221
    ## 20                  Municipality       15569000/11920
    ## 21                 City-province        11462000/9965
    ## 22         City (sub-provincial)        14498400/7434
    ## 23                          City         3990456/1214
    ## 24                  Federal city        13200000/2511
    ## 25         City (sub-provincial)        12528300/2050
    ## 26             Metropolitan city        11126000/1772
    ## 27                  Municipality          8443675/709
    ## 28                       Commune          2148271/105
    ## 29              Capital District         7963000/1587
    ## 30        Special capital region         10154134/664
    ## 31                  Municipality          6727000/426
    ## 32     Metropolitan municipality         8894000/2672
    ## 33   Special administrative area         5782000/1569
    ## 34                  Special city          9806000/605
    ## 35               Designated city          2320361/326
    ## 36                  Municipality          6993262/650
    ## 37                  Capital city         8825001/1572
    ## 38                  Capital city          9033003/751
    ## 39                          City          2705994/589
    ## 40         City (sub-provincial)       16044700/14378
    ## 41         City (sub-provincial)         7260000/6582
    ## 42         City (sub-provincial)        10892900/8494
    ## 43                  Municipality         7431000/2061
    ## 44                  Municipality          2165867/116
    ## 45                  Municipality          5570585/464
    ## 46                          City          1768000/243
    ## 47         City (sub-provincial)        8989000/10135
    ## 48 Special administrative region         7298600/1104
    ## 49         Prefecture-level city         8342500/2465
    ## 50         City (sub-provincial)        9468000/16596
    ## 51         City (sub-provincial)         7197394/3848
    ## 52         City (sub-provincial)        8294000/12980
    ## 53                  Municipality         6694000/1913
    ## 54             Urban governorate         8126755/5200
    ## 55                City (commune)            236453/22
    ## 56                  Municipality          4466826/327
    ## 57                  Municipality          3266126/606
    ## 58         City (sub-provincial)        10721700/8488
    ## 59                  Municipality          3124458/276
    ## 60         City (sub-provincial)       10635971/53068
    ## 61                          City         2325502/1553
    ## 62                          City          1345047/882
    ## 63                          City          2731571/630
    ## 64                          <NA>         4364541/1393
    ## 65                          <NA>            470914/93
    ## 66                          <NA>          2502557/331
    ## 67                       Country          5638700/726
    ## 68      Consolidated city-county          1526006/370
    ## 69                          <NA>           420003/354
    ## 70               Designated city          1588924/343
    ## 71                          <NA>         639598/22142
    ## 72                  Municipality          1620343/101
    ## 73     Metropolitan municipality                 <NA>
    ## 74                  Federal city                 <NA>
    ## 75         City (sub-provincial)                 <NA>
    ## 76         City (sub-provincial)                 <NA>
    ## 77              Federal district           702455/177
    ## 78                          City                 <NA>
    ## 79             Urban governorate                 <NA>
    ## 80         City (sub-provincial)        8700000/10244
    ## 81                  Municipality          1460148/151

Read documentation on the `separate()` function from tidyr. This
function allows you to separate a character column of a dataset into
multiple columns using a regular expression to define the separation.
Using the separate function and a regular expression, separate the
`Location` column into `City` and `State`.

``` r
population %>%  
  separate(Location, c("City", "State"), sep = ",\\s(?=[^,]+$)")
```

    ##                City          State UN.2018.population.estimates
    ## 1             Tokyo          Japan                     37400068
    ## 2             Delhi          India                     28514000
    ## 3          Shanghai          China                     25582000
    ## 4         São Paulo         Brazil                     21650000
    ## 5       Mexico City         Mexico                     21581000
    ## 6             Cairo          Egypt                     20076000
    ## 7            Mumbai          India                     19980000
    ## 8           Beijing          China                     19618000
    ## 9             Dhaka     Bangladesh                     19578000
    ## 10            Osaka          Japan                     19281000
    ## 11    New York City  United States                     18819000
    ## 12          Karachi       Pakistan                     15400000
    ## 13     Buenos Aires      Argentina                     14967000
    ## 14        Chongqing          China                     14838000
    ## 15         Istanbul         Turkey                     14751000
    ## 16          Kolkata          India                     14681000
    ## 17           Manila    Philippines                     13482000
    ## 18            Lagos        Nigeria                     13463000
    ## 19   Rio de Janeiro         Brazil                     13293000
    ## 20          Tianjin          China                     13215000
    ## 21         Kinshasa       DR Congo                     13171000
    ## 22        Guangzhou          China                     12638000
    ## 23      Los Angeles  United States                     12458000
    ## 24           Moscow         Russia                     12410000
    ## 25         Shenzhen          China                     11908000
    ## 26           Lahore       Pakistan                     11738000
    ## 27        Bangalore          India                     11440000
    ## 28            Paris         France                     10901000
    ## 29           Bogotá       Colombia                     10574000
    ## 30          Jakarta      Indonesia                     10517000
    ## 31          Chennai          India                     10456000
    ## 32             Lima           Peru                     10391000
    ## 33          Bangkok       Thailand                     10156000
    ## 34            Seoul    South Korea                      9963000
    ## 35           Nagoya          Japan                      9507000
    ## 36        Hyderabad          India                      9482000
    ## 37           London United Kingdom                      9046000
    ## 38           Tehran           Iran                      8896000
    ## 39          Chicago  United States                      8864000
    ## 40          Chengdu          China                      8813000
    ## 41          Nanjing          China                      8245000
    ## 42            Wuhan          China                      8176000
    ## 43 Ho Chi Minh City        Vietnam                      8145000
    ## 44           Luanda         Angola                      7774000
    ## 45        Ahmedabad          India                      7681000
    ## 46     Kuala Lumpur       Malaysia                      7564000
    ## 47            Xi'an          China                      7444000
    ## 48        Hong Kong          China                      7429000
    ## 49         Dongguan          China                      7360000
    ## 50         Hangzhou          China                      7236000
    ## 51           Foshan          China                      7236000
    ## 52         Shenyang          China                      6921000
    ## 53           Riyadh   Saudi Arabia                      6907000
    ## 54          Baghdad           Iraq                      6812000
    ## 55         Santiago          Chile                      6680000
    ## 56            Surat          India                      6564000
    ## 57           Madrid          Spain                      6497000
    ## 58           Suzhou          China                      6339000
    ## 59             Pune          India                      6276000
    ## 60           Harbin          China                      6115000
    ## 61          Houston  United States                      6115000
    ## 62           Dallas  United States                      6099000
    ## 63          Toronto         Canada                      6082000
    ## 64    Dar es Salaam       Tanzania                      6048000
    ## 65            Miami  United States                      6036000
    ## 66   Belo Horizonte         Brazil                      5972000
    ## 67        Singapore      Singapore                      5792000
    ## 68     Philadelphia  United States                      5695000
    ## 69          Atlanta  United States                      5572000
    ## 70          Fukuoka          Japan                      5551000
    ## 71         Khartoum          Sudan                      5534000
    ## 72        Barcelona          Spain                      5494000
    ## 73     Johannesburg   South Africa                      5486000
    ## 74 Saint Petersburg         Russia                      5383000
    ## 75          Qingdao          China                      5381000
    ## 76           Dalian          China                      5300000
    ## 77 Washington, D.C.  United States                      5207000
    ## 78           Yangon        Myanmar                      5157000
    ## 79       Alexandria          Egypt                      5086000
    ## 80            Jinan          China                      5052000
    ## 81      Guadalajara         Mexico                      5023000
    ##           City.Proper.Definition Population.per.Sq.km
    ## 1          Metropolis prefecture        13515271/2191
    ## 2     National capital territory        16753235/1484
    ## 3                   Municipality        24183000/6341
    ## 4                   Municipality        12252023/1521
    ## 5                     City-state         8918653/1485
    ## 6              Urban governorate         9500000/3085
    ## 7                   Municipality         12478447/603
    ## 8                   Municipality       21707000/16411
    ## 9                   Capital city          8906039/338
    ## 10               Designated city          2725006/225
    ## 11                          City          8398748/786
    ## 12             Metropolitan city        14910352/3530
    ## 13               Autonomous city          3054300/203
    ## 14                  Municipality       30165500/82403
    ## 15     Metropolitan municipality        15029231/5196
    ## 16                  Municipality          4496694/205
    ## 17                  Capital city           1780148/43
    ## 18                          <NA>                 <NA>
    ## 19                  Municipality         6520000/1221
    ## 20                  Municipality       15569000/11920
    ## 21                 City-province        11462000/9965
    ## 22         City (sub-provincial)        14498400/7434
    ## 23                          City         3990456/1214
    ## 24                  Federal city        13200000/2511
    ## 25         City (sub-provincial)        12528300/2050
    ## 26             Metropolitan city        11126000/1772
    ## 27                  Municipality          8443675/709
    ## 28                       Commune          2148271/105
    ## 29              Capital District         7963000/1587
    ## 30        Special capital region         10154134/664
    ## 31                  Municipality          6727000/426
    ## 32     Metropolitan municipality         8894000/2672
    ## 33   Special administrative area         5782000/1569
    ## 34                  Special city          9806000/605
    ## 35               Designated city          2320361/326
    ## 36                  Municipality          6993262/650
    ## 37                  Capital city         8825001/1572
    ## 38                  Capital city          9033003/751
    ## 39                          City          2705994/589
    ## 40         City (sub-provincial)       16044700/14378
    ## 41         City (sub-provincial)         7260000/6582
    ## 42         City (sub-provincial)        10892900/8494
    ## 43                  Municipality         7431000/2061
    ## 44                  Municipality          2165867/116
    ## 45                  Municipality          5570585/464
    ## 46                          City          1768000/243
    ## 47         City (sub-provincial)        8989000/10135
    ## 48 Special administrative region         7298600/1104
    ## 49         Prefecture-level city         8342500/2465
    ## 50         City (sub-provincial)        9468000/16596
    ## 51         City (sub-provincial)         7197394/3848
    ## 52         City (sub-provincial)        8294000/12980
    ## 53                  Municipality         6694000/1913
    ## 54             Urban governorate         8126755/5200
    ## 55                City (commune)            236453/22
    ## 56                  Municipality          4466826/327
    ## 57                  Municipality          3266126/606
    ## 58         City (sub-provincial)        10721700/8488
    ## 59                  Municipality          3124458/276
    ## 60         City (sub-provincial)       10635971/53068
    ## 61                          City         2325502/1553
    ## 62                          City          1345047/882
    ## 63                          City          2731571/630
    ## 64                          <NA>         4364541/1393
    ## 65                          <NA>            470914/93
    ## 66                          <NA>          2502557/331
    ## 67                       Country          5638700/726
    ## 68      Consolidated city-county          1526006/370
    ## 69                          <NA>           420003/354
    ## 70               Designated city          1588924/343
    ## 71                          <NA>         639598/22142
    ## 72                  Municipality          1620343/101
    ## 73     Metropolitan municipality                 <NA>
    ## 74                  Federal city                 <NA>
    ## 75         City (sub-provincial)                 <NA>
    ## 76         City (sub-provincial)                 <NA>
    ## 77              Federal district           702455/177
    ## 78                          City                 <NA>
    ## 79             Urban governorate                 <NA>
    ## 80         City (sub-provincial)        8700000/10244
    ## 81                  Municipality          1460148/151

``` r
  #separate(Location, c("City", "State"), sep = ",(?=[^,]+$)")   
  #separate(Location, c("City", "State"), sep = ",.(?=[^,]+$)") 
```
