transform-exercises
================

# Grammar of Data Manipulation

These exercises cover concepts covered in Chapter 5 of R for Data
Science (<https://r4ds.had.co.nz/transform.html>). Please answer all the
questions by using tidyverse grammar. Documentation of the functions you
will use can be found in the dplyr package documentation
(<https://dplyr.tidyverse.org/>). Do feel free to post questions on
Slack as well.

One additional helpful package will be janitor
(<https://github.com/sfirke/janitor>), in particular the clean\_names
function. The data has columns names with spaces which is annoying to
deal with–clean\_names handles that.

For each problem, create an issue with the text describing the problem.
Use GH Flow (create a branch for each problem in turn, close with a
commit message, and create a pull request that you yourself merge).

## Load Libraries

``` r
library(tidyverse)
library(dplyr)
library(janitor)
```

## Import Data

The data is from <https://www.kaggle.com/abecklas/fifa-world-cup> and
the 2018 world cup data is added.

``` r
worldcups <- read.csv("WorldCups.csv")
worldcups_match <- read.csv("WorldCupMatches.csv")
wc <- read.csv("WorldCups.csv")
wc_match <- read.csv("WorldCupMatches.csv")
```

``` r
head(worldcups) 
```

    ##   Year     Country     Winner     Runners.Up   Third     Fourth GoalsScored
    ## 1 1930     Uruguay    Uruguay      Argentina     USA Yugoslavia          70
    ## 2 1934       Italy      Italy Czechoslovakia Germany    Austria          70
    ## 3 1938      France      Italy        Hungary  Brazil     Sweden          84
    ## 4 1950      Brazil    Uruguay         Brazil  Sweden      Spain          88
    ## 5 1954 Switzerland Germany FR        Hungary Austria    Uruguay         140
    ## 6 1958      Sweden     Brazil         Sweden  France Germany FR         126
    ##   QualifiedTeams MatchesPlayed
    ## 1             13            18
    ## 2             16            17
    ## 3             15            18
    ## 4             13            22
    ## 5             16            26
    ## 6             16            35

``` r
view(worldcups)
head(worldcups_match)
```

    ##   Year             Datetime   Stage        Stadium        City Home.Team.Name
    ## 1 1930 13 Jul 1930 - 15:00  Group 1        Pocitos Montevideo          France
    ## 2 1930 13 Jul 1930 - 15:00  Group 4 Parque Central Montevideo             USA
    ## 3 1930 14 Jul 1930 - 12:45  Group 2 Parque Central Montevideo      Yugoslavia
    ## 4 1930 14 Jul 1930 - 14:50  Group 3        Pocitos Montevideo         Romania
    ## 5 1930 15 Jul 1930 - 16:00  Group 1 Parque Central Montevideo       Argentina
    ## 6 1930 16 Jul 1930 - 14:45  Group 1 Parque Central Montevideo           Chile
    ##   Home.Team.Goals Away.Team.Goals Away.Team.Name                Referee
    ## 1               4               1         Mexico LOMBARDI Domingo (URU)
    ## 2               3               0        Belgium      MACIAS Jose (ARG)
    ## 3               2               1         Brazil    TEJADA Anibal (URU)
    ## 4               3               1           Peru  WARNKEN Alberto (CHI)
    ## 5               1               0         France    REGO Gilberto (BRA)
    ## 6               3               0         Mexico  CRISTOPHE Henry (BEL)
    ##                Assistant.1                Assistant.2 MatchID
    ## 1    CRISTOPHE Henry (BEL)        REGO Gilberto (BRA)    1096
    ## 2 MATEUCCI Francisco (URU)      WARNKEN Alberto (CHI)    1090
    ## 3  VALLARINO Ricardo (URU)        BALWAY Thomas (FRA)    1093
    ## 4      LANGENUS Jean (BEL)   MATEUCCI Francisco (URU)    1098
    ## 5     SAUCEDO Ulises (BOL) RADULESCU Constantin (ROU)    1085
    ## 6  APHESTEGUY Martin (URU)        LANGENUS Jean (BEL)    1095

``` r
view(worldcups_match)
```

## Problem 1

Find all countries that have won world cup and the number of World Cup
titles won by each country in descending order. Find top three world cup
winners. Return a dataframe with all countries, and note the answer in a
comment below your output.

(Note: Germany FR and Germany are considered as the same winner!)

``` r
wc$Winner <- str_replace_all(wc$Winner, "Germany FR", "Germany")
wc_winners <- wc %>% 
group_by(Winner) %>% 
 summarize(Number = n()) %>% 
arrange(desc(Number))
head(wc_winners, 3)
```

    ## # A tibble: 3 × 2
    ##   Winner  Number
    ##   <chr>    <int>
    ## 1 Brazil       5
    ## 2 Germany      4
    ## 3 Italy        4

Brazil has won the most world cups with 5 wins, followed by Germany &
Italy with 4 each

## Problem 2

Which team hasn’t won a World Cup on their home turf?

(Note: Germany FR and Germany are considered as the same winner!)

``` r
worldcups$Winner <- gsub('Germany FR', 'Germany', worldcups$Winner)
win_on_truf <- worldcups %>% 
 filter(Country == Winner )  
 in_or_not <- !(worldcups$Winner%in%win_on_truf$Winner) 
 not_on_truf_winner <- worldcups$Winner[in_or_not]
unique(not_on_truf_winner) 
```

    ## [1] "Brazil" "Spain"

## Problem 3

Which world cup has highest average goals per game? Please note the
year, host and the average goal

``` r
wc_goals <- wc %>%
mutate(avg_goals = GoalsScored/MatchesPlayed) %>%
arrange(desc(avg_goals)) %>% 
select(Year, Country, avg_goals) %>% 
head(1)
wc_goals
```

    ##   Year     Country avg_goals
    ## 1 1954 Switzerland  5.384615

## Problem 4

Which world cup final has most scores? Please list the date and teams of
this final.

``` r
library(janitor)
WCfinals = filter(worldcups_match, Stage == "Final")
WCfinals = clean_names(WCfinals)
WCfinals = mutate(WCfinals, total_score = home_team_goals + away_team_goals)
arrange(WCfinals, desc(total_score)) %>% 
filter(total_score == max(total_score))
```

    ##   year             datetime stage         stadium   city home_team_name
    ## 1 1958 29 Jun 1958 - 15:00  Final Rasunda Stadium Solna          Brazil
    ##   home_team_goals away_team_goals away_team_name              referee
    ## 1               5               2         Sweden GUIGUE Maurice (FRA)
    ##          assistant_1            assistant_2 match_id total_score
    ## 1 DUSCH Albert (GER) GARDEAZABAL Juan (ESP)     1343           7

The highest scores in a world cup finals was on June 29th 1958, where
Brazil beat Sweden 5-2.

## Problem 5

What is the biggest goal difference in World Cup? Include the year,
teams and goals of these matches.

Note: Only return the information about matches with biggest goal
difference

``` r
library(janitor)
WorldCupMatches = clean_names(worldcups_match)
WorldCupMatches = mutate(WorldCupMatches, goal_diff = abs(home_team_goals - away_team_goals))
head(arrange(WorldCupMatches, desc(goal_diff))) %>% 
 filter(goal_diff == max(goal_diff))
```

    ##   year             datetime   stage       stadium           city home_team_name
    ## 1 1954 17 Jun 1954 - 18:00  Group 2      Hardturm        Zurich         Hungary
    ## 2 1974 18 Jun 1974 - 19:30  Group 2   Parkstadion Gelsenkirchen      Yugoslavia
    ## 3 1982 15 Jun 1982 - 21:00  Group 3 Nuevo Estadio         Elche         Hungary
    ##   home_team_goals away_team_goals away_team_name                referee
    ## 1               9               0 Korea Republic VINCENTI Raymond (FRA)
    ## 2               9               0          Zaire     DELGADO Omar (COL)
    ## 3              10               1    El Salvador   AL DOY Ebrahim (BHR)
    ##               assistant_1                 assistant_2 match_id goal_diff
    ## 1 VON GUNTER Albert (SUI)          STEINER Carl (AUT)     1294         9
    ## 2 LLOBREGAT Vicente (VEN)    BARRETO RUIZ Ramon (URU)     2186         9
    ## 3    CORVER Charles (NED) LUND-SORENSEN Henning (DEN)      896         9

Three matches are tied for the largest goal differential at 9: 1954
Hungary (9) - Korea (0), 1974 Yugoslavia (9) - Zaire (0), and 1982
Hungary (10) - El Salvador (1).

## Problem 6

How many World Cup finals have been decided by penalty shootout? (Home
and Away teams have the same number of goals.) Also please refer to
WorldCups dataset to check the winner!

``` r
Ps_in_finals <- worldcups_match %>% 
  filter(Stage == "Final" & Home.Team.Goals == Away.Team.Goals)  
Ps_in_finals %>% 
  summarise(Number=n()) 
```

    ##   Number
    ## 1      2

``` r
Winner_by_Ps <- merge(worldcups, Ps_in_finals, by='Year')
Winner_by_Ps %>% 
  select(Winner)
```

    ##   Winner
    ## 1 Brazil
    ## 2  Italy

## Problem 7

Which World Cup did not have a final? Please list the year of that world
cup.

``` r
Wc_have_final <- worldcups_match %>% 
  filter(Stage == 'Final')
in_or_not <-worldcups_match$Year%in%Wc_have_final$Year
no_final_year <- worldcups_match$Year[!in_or_not]
unique(no_final_year)
```

    ## [1] 1950

## Problem 8

Which world cup had the biggest goal difference on average and which
worldcup had the least goal difference on average? Include the year, the
difference on average and the variance of goal difference.

``` r
wc_match <- as.data.frame(wc_match)
wc_goal_diff <- wc_match %>% 
  clean_names() %>% 
  mutate(GD = abs(home_team_goals - away_team_goals)) %>% 
  group_by(year) %>% 
  summarize(mean_GD = mean(GD), var_GD = var(GD)) %>% 
  select(year, mean_GD, var_GD)

# Highest GD on average
high_GD <- wc_goal_diff %>% 
  arrange(desc(mean_GD)) %>%
  head(1)

# Lowest GD on average
low_GD <- wc_goal_diff %>% 
  arrange(mean_GD) %>% 
  head(1)

# printing high GD
high_GD
```

    ## # A tibble: 1 × 3
    ##    year mean_GD var_GD
    ##   <int>   <dbl>  <dbl>
    ## 1  1954       3   5.36

``` r
# printing low GD
low_GD
```

    ## # A tibble: 1 × 3
    ##    year mean_GD var_GD
    ##   <int>   <dbl>  <dbl>
    ## 1  1990    1.21   1.11

The 1954 world cup has the highest goal differences per game with a mean
of 3.0 goal difference and a variance of 5.36 goal difference.

The 1990 world cup has the lowest goal differences per game with a mean
of 1.21 goal difference and a variance of 1.11 goal difference.

## Problem 9

Choose your favorite team and tell me what do you find(ex: the average
score, the rank, etc)

``` r
#Because I am totally a F.Torres fan, I choose Spain as my favorite team.
#Calculate the Average scores of Spain per game in World Cups

#Since when we calculate the average goals and sessions, we do not think that the merged or split countries as the same. So we do not merge or split such countries, suah as Germany FR and German DR. (This is different from the championship succession system when calculating the championship above.)

home_team <- worldcups_match %>% 
  group_by(Home.Team.Name) %>% 
  summarise(home_team_goals_by_team = sum(Home.Team.Goals))

away_team <- worldcups_match %>% 
  group_by(Away.Team.Name) %>% 
  summarise(away_team_goals_by_team = sum(Away.Team.Goals))

names(home_team)<-c("team_name","home_team_goals_by_team")
names(away_team)<-c("team_name","away_team_goals_by_team")
both_h_a_team <- merge(home_team, away_team, by='team_name')
both_h_a_team[is.na(both_h_a_team)] <- 0

all_team <- both_h_a_team %>% 
  mutate(`team_total_goals` = both_h_a_team$home_team_goals_by_team + both_h_a_team$away_team_goals_by_team)


home_session <- worldcups_match %>% 
  group_by(Home.Team.Name) %>% 
  summarise(home_team_sessions_by_team=n())
away_session <- worldcups_match %>% 
  group_by(Away.Team.Name) %>% 
  summarise(away_team_sessions_by_team=n())

names(home_session)<-c("team_name","home_team_sessions_by_team")
names(away_session)<-c("team_name","away_team_sessions_by_team")
both_h_a_sessions <- merge(home_session, away_session, by='team_name')
both_h_a_sessions[is.na(both_h_a_sessions)]  <- 0

all_sessions <- both_h_a_sessions %>% 
  mutate(`team_total_sessions` = both_h_a_sessions$home_team_sessions_by_team + both_h_a_sessions$away_team_sessions_by_team)
  
both_team_sessions <- merge(all_team, all_sessions, by='team_name') %>% 
  mutate(`team_average_goals` = team_total_goals/team_total_sessions) %>% 
  mutate(Rank = min_rank(desc(`team_average_goals`))) %>%  
  arrange(desc(`team_average_goals`)) %>% 
  select(team_name, team_total_goals, team_total_sessions, team_average_goals, Rank)
both_team_sessions 
```

    ##                     team_name team_total_goals team_total_sessions
    ## 1                     Hungary               87                  32
    ## 2                  Germany FR              131                  62
    ## 3                      Brazil              229                 109
    ## 4                     Germany               95                  47
    ## 5                      Turkey               20                  10
    ## 6                      France              120                  66
    ## 7                 Netherlands               86                  50
    ## 8                      Russia               24                  14
    ## 9                Soviet Union               53                  31
    ## 10                  Argentina              137                  81
    ## 11                       Cuba                5                   3
    ## 12                   Portugal               49                  30
    ## 13                 Yugoslavia               60                  37
    ## 14                      Spain               99                  63
    ## 15                     Sweden               80                  51
    ## 16                    Uruguay               87                  56
    ## 17                      Italy              128                  83
    ## 18                    Croatia               35                  23
    ## 19                    Denmark               30                  20
    ## 20                    Austria               43                  29
    ## 21             Czechoslovakia               44                  30
    ## 22                   Colombia               32                  22
    ## 23              C�te d'Ivoire               13                   9
    ## 24                    Romania               30                  21
    ## 25                    Belgium               68                  48
    ## 26                    Senegal               11                   8
    ## 27                     Poland               46                  34
    ## 28                Switzerland               50                  37
    ## 29 rn">Bosnia and Herzegovina                4                   3
    ## 30                    England               91                  69
    ## 31                   Slovakia                5                   4
    ## 32               South Africa               11                   9
    ## 33                      Chile               40                  33
    ## 34                       Peru               21                  18
    ## 35                        USA               37                  33
    ## 36                   Paraguay               30                  27
    ## 37                    Nigeria               23                  21
    ## 38                   Scotland               25                  23
    ## 39                      Ghana               13                  12
    ## 40                 Costa Rica               19                  18
    ## 41                     Mexico               60                  57
    ## 42                    Algeria               13                  13
    ## 43             Czech Republic                3                   3
    ## 44                    Ecuador               10                  10
    ## 45                    Jamaica                3                   3
    ## 46             Korea Republic               34                  34
    ## 47           Northern Ireland               13                  13
    ## 48                    Ukraine                5                   5
    ## 49                      Japan               20                  21
    ## 50                    Morocco               14                  16
    ## 51                     Norway                7                   8
    ## 52                    Tunisia               13                  15
    ## 53                  Korea DPR                6                   7
    ## 54                   Bulgaria               22                  26
    ## 55                  German DR                5                   6
    ## 56                       Iran                5                   6
    ## 57                   Slovenia                5                   6
    ## 58                  Australia               13                  16
    ## 59                      Wales                4                   5
    ## 60                   Cameroon               18                  23
    ## 61    rn">Republic of Ireland               10                  13
    ## 62                      Egypt                5                   7
    ## 63               Saudi Arabia               11                  16
    ## 64                      Haiti                2                   3
    ## 65                    Iceland                2                   3
    ## 66                New Zealand                4                   6
    ## 67                     Panama                2                   3
    ## 68  rn">Serbia and Montenegro                2                   3
    ## 69   rn">United Arab Emirates                2                   3
    ## 70                     Serbia                4                   6
    ## 71                     Greece                5                  10
    ## 72                    IR Iran                4                   9
    ## 73                     Angola                1                   3
    ## 74                   Honduras                3                   9
    ## 75                       Iraq                1                   3
    ## 76                       Togo                1                   3
    ## 77                    Bolivia                1                   6
    ## 78                     Canada                0                   3
    ## 79                   China PR                0                   3
    ## 80    rn">Trinidad and Tobago                0                   3
    ## 81                      Zaire                0                   3
    ##    team_average_goals Rank
    ## 1           2.7187500    1
    ## 2           2.1129032    2
    ## 3           2.1009174    3
    ## 4           2.0212766    4
    ## 5           2.0000000    5
    ## 6           1.8181818    6
    ## 7           1.7200000    7
    ## 8           1.7142857    8
    ## 9           1.7096774    9
    ## 10          1.6913580   10
    ## 11          1.6666667   11
    ## 12          1.6333333   12
    ## 13          1.6216216   13
    ## 14          1.5714286   14
    ## 15          1.5686275   15
    ## 16          1.5535714   16
    ## 17          1.5421687   17
    ## 18          1.5217391   18
    ## 19          1.5000000   19
    ## 20          1.4827586   20
    ## 21          1.4666667   21
    ## 22          1.4545455   22
    ## 23          1.4444444   23
    ## 24          1.4285714   24
    ## 25          1.4166667   25
    ## 26          1.3750000   26
    ## 27          1.3529412   27
    ## 28          1.3513514   28
    ## 29          1.3333333   29
    ## 30          1.3188406   30
    ## 31          1.2500000   31
    ## 32          1.2222222   32
    ## 33          1.2121212   33
    ## 34          1.1666667   34
    ## 35          1.1212121   35
    ## 36          1.1111111   36
    ## 37          1.0952381   37
    ## 38          1.0869565   38
    ## 39          1.0833333   39
    ## 40          1.0555556   40
    ## 41          1.0526316   41
    ## 42          1.0000000   42
    ## 43          1.0000000   42
    ## 44          1.0000000   42
    ## 45          1.0000000   42
    ## 46          1.0000000   42
    ## 47          1.0000000   42
    ## 48          1.0000000   42
    ## 49          0.9523810   49
    ## 50          0.8750000   50
    ## 51          0.8750000   50
    ## 52          0.8666667   52
    ## 53          0.8571429   53
    ## 54          0.8461538   54
    ## 55          0.8333333   55
    ## 56          0.8333333   55
    ## 57          0.8333333   55
    ## 58          0.8125000   58
    ## 59          0.8000000   59
    ## 60          0.7826087   60
    ## 61          0.7692308   61
    ## 62          0.7142857   62
    ## 63          0.6875000   63
    ## 64          0.6666667   64
    ## 65          0.6666667   64
    ## 66          0.6666667   64
    ## 67          0.6666667   64
    ## 68          0.6666667   64
    ## 69          0.6666667   64
    ## 70          0.6666667   64
    ## 71          0.5000000   71
    ## 72          0.4444444   72
    ## 73          0.3333333   73
    ## 74          0.3333333   73
    ## 75          0.3333333   73
    ## 76          0.3333333   73
    ## 77          0.1666667   77
    ## 78          0.0000000   78
    ## 79          0.0000000   78
    ## 80          0.0000000   78
    ## 81          0.0000000   78

``` r
both_team_sessions %>% 
  filter(team_name == 'Spain')
```

    ##   team_name team_total_goals team_total_sessions team_average_goals Rank
    ## 1     Spain               99                  63           1.571429   14
