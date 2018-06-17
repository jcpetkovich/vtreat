vtreat on Spark
================

``` r
library("vtreat")
packageVersion("vtreat")
```

    ## [1] '1.2.0'

``` r
library("rquery")
packageVersion("rquery")
```

    ## [1] '0.5.0'

``` r
packageVersion("cdata")
```

    ## [1] '0.7.2'

``` r
packageVersion("sparklyr")
```

    ## [1] '0.8.4'

``` r
db <- sparklyr::spark_connect(version='2.2.0', 
                              master = "local")
db_opts <- rq_connection_tests(db)
options(db_opts)
```

``` r
tmp_name_gen <- wrapr::mk_tmp_name_source("kddvtreat")

d <- db_td(db, "kdd2009") %.>%
  extend_nse(., sample_col = random())

cat(format(d))
```

    ## table('kdd2009'; 
    ##   Var1,
    ##   Var2,
    ##   Var3,
    ##   Var4,
    ##   Var5,
    ##   Var6,
    ##   Var7,
    ##   Var8,
    ##   Var9,
    ##   Var10,
    ##   Var11,
    ##   Var12,
    ##   Var13,
    ##   Var14,
    ##   Var15,
    ##   Var16,
    ##   Var17,
    ##   Var18,
    ##   Var19,
    ##   Var20,
    ##   ...) %.>%
    ##  extend(.,
    ##   sample_col := random())

``` r
cat(to_sql(d, db))
```

    ## SELECT
    ##  `Var1`,
    ##  `Var2`,
    ##  `Var3`,
    ##  `Var4`,
    ##  `Var5`,
    ##  `Var6`,
    ##  `Var7`,
    ##  `Var8`,
    ##  `Var9`,
    ##  `Var10`,
    ##  `Var11`,
    ##  `Var12`,
    ##  `Var13`,
    ##  `Var14`,
    ##  `Var15`,
    ##  `Var16`,
    ##  `Var17`,
    ##  `Var18`,
    ##  `Var19`,
    ##  `Var20`,
    ##  `Var21`,
    ##  `Var22`,
    ##  `Var23`,
    ##  `Var24`,
    ##  `Var25`,
    ##  `Var26`,
    ##  `Var27`,
    ##  `Var28`,
    ##  `Var29`,
    ##  `Var30`,
    ##  `Var31`,
    ##  `Var32`,
    ##  `Var33`,
    ##  `Var34`,
    ##  `Var35`,
    ##  `Var36`,
    ##  `Var37`,
    ##  `Var38`,
    ##  `Var39`,
    ##  `Var40`,
    ##  `Var41`,
    ##  `Var42`,
    ##  `Var43`,
    ##  `Var44`,
    ##  `Var45`,
    ##  `Var46`,
    ##  `Var47`,
    ##  `Var48`,
    ##  `Var49`,
    ##  `Var50`,
    ##  `Var51`,
    ##  `Var52`,
    ##  `Var53`,
    ##  `Var54`,
    ##  `Var55`,
    ##  `Var56`,
    ##  `Var57`,
    ##  `Var58`,
    ##  `Var59`,
    ##  `Var60`,
    ##  `Var61`,
    ##  `Var62`,
    ##  `Var63`,
    ##  `Var64`,
    ##  `Var65`,
    ##  `Var66`,
    ##  `Var67`,
    ##  `Var68`,
    ##  `Var69`,
    ##  `Var70`,
    ##  `Var71`,
    ##  `Var72`,
    ##  `Var73`,
    ##  `Var74`,
    ##  `Var75`,
    ##  `Var76`,
    ##  `Var77`,
    ##  `Var78`,
    ##  `Var79`,
    ##  `Var80`,
    ##  `Var81`,
    ##  `Var82`,
    ##  `Var83`,
    ##  `Var84`,
    ##  `Var85`,
    ##  `Var86`,
    ##  `Var87`,
    ##  `Var88`,
    ##  `Var89`,
    ##  `Var90`,
    ##  `Var91`,
    ##  `Var92`,
    ##  `Var93`,
    ##  `Var94`,
    ##  `Var95`,
    ##  `Var96`,
    ##  `Var97`,
    ##  `Var98`,
    ##  `Var99`,
    ##  `Var100`,
    ##  `Var101`,
    ##  `Var102`,
    ##  `Var103`,
    ##  `Var104`,
    ##  `Var105`,
    ##  `Var106`,
    ##  `Var107`,
    ##  `Var108`,
    ##  `Var109`,
    ##  `Var110`,
    ##  `Var111`,
    ##  `Var112`,
    ##  `Var113`,
    ##  `Var114`,
    ##  `Var115`,
    ##  `Var116`,
    ##  `Var117`,
    ##  `Var118`,
    ##  `Var119`,
    ##  `Var120`,
    ##  `Var121`,
    ##  `Var122`,
    ##  `Var123`,
    ##  `Var124`,
    ##  `Var125`,
    ##  `Var126`,
    ##  `Var127`,
    ##  `Var128`,
    ##  `Var129`,
    ##  `Var130`,
    ##  `Var131`,
    ##  `Var132`,
    ##  `Var133`,
    ##  `Var134`,
    ##  `Var135`,
    ##  `Var136`,
    ##  `Var137`,
    ##  `Var138`,
    ##  `Var139`,
    ##  `Var140`,
    ##  `Var141`,
    ##  `Var142`,
    ##  `Var143`,
    ##  `Var144`,
    ##  `Var145`,
    ##  `Var146`,
    ##  `Var147`,
    ##  `Var148`,
    ##  `Var149`,
    ##  `Var150`,
    ##  `Var151`,
    ##  `Var152`,
    ##  `Var153`,
    ##  `Var154`,
    ##  `Var155`,
    ##  `Var156`,
    ##  `Var157`,
    ##  `Var158`,
    ##  `Var159`,
    ##  `Var160`,
    ##  `Var161`,
    ##  `Var162`,
    ##  `Var163`,
    ##  `Var164`,
    ##  `Var165`,
    ##  `Var166`,
    ##  `Var167`,
    ##  `Var168`,
    ##  `Var169`,
    ##  `Var170`,
    ##  `Var171`,
    ##  `Var172`,
    ##  `Var173`,
    ##  `Var174`,
    ##  `Var175`,
    ##  `Var176`,
    ##  `Var177`,
    ##  `Var178`,
    ##  `Var179`,
    ##  `Var180`,
    ##  `Var181`,
    ##  `Var182`,
    ##  `Var183`,
    ##  `Var184`,
    ##  `Var185`,
    ##  `Var186`,
    ##  `Var187`,
    ##  `Var188`,
    ##  `Var189`,
    ##  `Var190`,
    ##  `Var191`,
    ##  `Var192`,
    ##  `Var193`,
    ##  `Var194`,
    ##  `Var195`,
    ##  `Var196`,
    ##  `Var197`,
    ##  `Var198`,
    ##  `Var199`,
    ##  `Var200`,
    ##  `Var201`,
    ##  `Var202`,
    ##  `Var203`,
    ##  `Var204`,
    ##  `Var205`,
    ##  `Var206`,
    ##  `Var207`,
    ##  `Var208`,
    ##  `Var209`,
    ##  `Var210`,
    ##  `Var211`,
    ##  `Var212`,
    ##  `Var213`,
    ##  `Var214`,
    ##  `Var215`,
    ##  `Var216`,
    ##  `Var217`,
    ##  `Var218`,
    ##  `Var219`,
    ##  `Var220`,
    ##  `Var221`,
    ##  `Var222`,
    ##  `Var223`,
    ##  `Var224`,
    ##  `Var225`,
    ##  `Var226`,
    ##  `Var227`,
    ##  `Var228`,
    ##  `Var229`,
    ##  `Var230`,
    ##  `churn`,
    ##  rand ( )  AS `sample_col`
    ## FROM (
    ##  SELECT
    ##   `kdd2009`.`Var1`,
    ##   `kdd2009`.`Var2`,
    ##   `kdd2009`.`Var3`,
    ##   `kdd2009`.`Var4`,
    ##   `kdd2009`.`Var5`,
    ##   `kdd2009`.`Var6`,
    ##   `kdd2009`.`Var7`,
    ##   `kdd2009`.`Var8`,
    ##   `kdd2009`.`Var9`,
    ##   `kdd2009`.`Var10`,
    ##   `kdd2009`.`Var11`,
    ##   `kdd2009`.`Var12`,
    ##   `kdd2009`.`Var13`,
    ##   `kdd2009`.`Var14`,
    ##   `kdd2009`.`Var15`,
    ##   `kdd2009`.`Var16`,
    ##   `kdd2009`.`Var17`,
    ##   `kdd2009`.`Var18`,
    ##   `kdd2009`.`Var19`,
    ##   `kdd2009`.`Var20`,
    ##   `kdd2009`.`Var21`,
    ##   `kdd2009`.`Var22`,
    ##   `kdd2009`.`Var23`,
    ##   `kdd2009`.`Var24`,
    ##   `kdd2009`.`Var25`,
    ##   `kdd2009`.`Var26`,
    ##   `kdd2009`.`Var27`,
    ##   `kdd2009`.`Var28`,
    ##   `kdd2009`.`Var29`,
    ##   `kdd2009`.`Var30`,
    ##   `kdd2009`.`Var31`,
    ##   `kdd2009`.`Var32`,
    ##   `kdd2009`.`Var33`,
    ##   `kdd2009`.`Var34`,
    ##   `kdd2009`.`Var35`,
    ##   `kdd2009`.`Var36`,
    ##   `kdd2009`.`Var37`,
    ##   `kdd2009`.`Var38`,
    ##   `kdd2009`.`Var39`,
    ##   `kdd2009`.`Var40`,
    ##   `kdd2009`.`Var41`,
    ##   `kdd2009`.`Var42`,
    ##   `kdd2009`.`Var43`,
    ##   `kdd2009`.`Var44`,
    ##   `kdd2009`.`Var45`,
    ##   `kdd2009`.`Var46`,
    ##   `kdd2009`.`Var47`,
    ##   `kdd2009`.`Var48`,
    ##   `kdd2009`.`Var49`,
    ##   `kdd2009`.`Var50`,
    ##   `kdd2009`.`Var51`,
    ##   `kdd2009`.`Var52`,
    ##   `kdd2009`.`Var53`,
    ##   `kdd2009`.`Var54`,
    ##   `kdd2009`.`Var55`,
    ##   `kdd2009`.`Var56`,
    ##   `kdd2009`.`Var57`,
    ##   `kdd2009`.`Var58`,
    ##   `kdd2009`.`Var59`,
    ##   `kdd2009`.`Var60`,
    ##   `kdd2009`.`Var61`,
    ##   `kdd2009`.`Var62`,
    ##   `kdd2009`.`Var63`,
    ##   `kdd2009`.`Var64`,
    ##   `kdd2009`.`Var65`,
    ##   `kdd2009`.`Var66`,
    ##   `kdd2009`.`Var67`,
    ##   `kdd2009`.`Var68`,
    ##   `kdd2009`.`Var69`,
    ##   `kdd2009`.`Var70`,
    ##   `kdd2009`.`Var71`,
    ##   `kdd2009`.`Var72`,
    ##   `kdd2009`.`Var73`,
    ##   `kdd2009`.`Var74`,
    ##   `kdd2009`.`Var75`,
    ##   `kdd2009`.`Var76`,
    ##   `kdd2009`.`Var77`,
    ##   `kdd2009`.`Var78`,
    ##   `kdd2009`.`Var79`,
    ##   `kdd2009`.`Var80`,
    ##   `kdd2009`.`Var81`,
    ##   `kdd2009`.`Var82`,
    ##   `kdd2009`.`Var83`,
    ##   `kdd2009`.`Var84`,
    ##   `kdd2009`.`Var85`,
    ##   `kdd2009`.`Var86`,
    ##   `kdd2009`.`Var87`,
    ##   `kdd2009`.`Var88`,
    ##   `kdd2009`.`Var89`,
    ##   `kdd2009`.`Var90`,
    ##   `kdd2009`.`Var91`,
    ##   `kdd2009`.`Var92`,
    ##   `kdd2009`.`Var93`,
    ##   `kdd2009`.`Var94`,
    ##   `kdd2009`.`Var95`,
    ##   `kdd2009`.`Var96`,
    ##   `kdd2009`.`Var97`,
    ##   `kdd2009`.`Var98`,
    ##   `kdd2009`.`Var99`,
    ##   `kdd2009`.`Var100`,
    ##   `kdd2009`.`Var101`,
    ##   `kdd2009`.`Var102`,
    ##   `kdd2009`.`Var103`,
    ##   `kdd2009`.`Var104`,
    ##   `kdd2009`.`Var105`,
    ##   `kdd2009`.`Var106`,
    ##   `kdd2009`.`Var107`,
    ##   `kdd2009`.`Var108`,
    ##   `kdd2009`.`Var109`,
    ##   `kdd2009`.`Var110`,
    ##   `kdd2009`.`Var111`,
    ##   `kdd2009`.`Var112`,
    ##   `kdd2009`.`Var113`,
    ##   `kdd2009`.`Var114`,
    ##   `kdd2009`.`Var115`,
    ##   `kdd2009`.`Var116`,
    ##   `kdd2009`.`Var117`,
    ##   `kdd2009`.`Var118`,
    ##   `kdd2009`.`Var119`,
    ##   `kdd2009`.`Var120`,
    ##   `kdd2009`.`Var121`,
    ##   `kdd2009`.`Var122`,
    ##   `kdd2009`.`Var123`,
    ##   `kdd2009`.`Var124`,
    ##   `kdd2009`.`Var125`,
    ##   `kdd2009`.`Var126`,
    ##   `kdd2009`.`Var127`,
    ##   `kdd2009`.`Var128`,
    ##   `kdd2009`.`Var129`,
    ##   `kdd2009`.`Var130`,
    ##   `kdd2009`.`Var131`,
    ##   `kdd2009`.`Var132`,
    ##   `kdd2009`.`Var133`,
    ##   `kdd2009`.`Var134`,
    ##   `kdd2009`.`Var135`,
    ##   `kdd2009`.`Var136`,
    ##   `kdd2009`.`Var137`,
    ##   `kdd2009`.`Var138`,
    ##   `kdd2009`.`Var139`,
    ##   `kdd2009`.`Var140`,
    ##   `kdd2009`.`Var141`,
    ##   `kdd2009`.`Var142`,
    ##   `kdd2009`.`Var143`,
    ##   `kdd2009`.`Var144`,
    ##   `kdd2009`.`Var145`,
    ##   `kdd2009`.`Var146`,
    ##   `kdd2009`.`Var147`,
    ##   `kdd2009`.`Var148`,
    ##   `kdd2009`.`Var149`,
    ##   `kdd2009`.`Var150`,
    ##   `kdd2009`.`Var151`,
    ##   `kdd2009`.`Var152`,
    ##   `kdd2009`.`Var153`,
    ##   `kdd2009`.`Var154`,
    ##   `kdd2009`.`Var155`,
    ##   `kdd2009`.`Var156`,
    ##   `kdd2009`.`Var157`,
    ##   `kdd2009`.`Var158`,
    ##   `kdd2009`.`Var159`,
    ##   `kdd2009`.`Var160`,
    ##   `kdd2009`.`Var161`,
    ##   `kdd2009`.`Var162`,
    ##   `kdd2009`.`Var163`,
    ##   `kdd2009`.`Var164`,
    ##   `kdd2009`.`Var165`,
    ##   `kdd2009`.`Var166`,
    ##   `kdd2009`.`Var167`,
    ##   `kdd2009`.`Var168`,
    ##   `kdd2009`.`Var169`,
    ##   `kdd2009`.`Var170`,
    ##   `kdd2009`.`Var171`,
    ##   `kdd2009`.`Var172`,
    ##   `kdd2009`.`Var173`,
    ##   `kdd2009`.`Var174`,
    ##   `kdd2009`.`Var175`,
    ##   `kdd2009`.`Var176`,
    ##   `kdd2009`.`Var177`,
    ##   `kdd2009`.`Var178`,
    ##   `kdd2009`.`Var179`,
    ##   `kdd2009`.`Var180`,
    ##   `kdd2009`.`Var181`,
    ##   `kdd2009`.`Var182`,
    ##   `kdd2009`.`Var183`,
    ##   `kdd2009`.`Var184`,
    ##   `kdd2009`.`Var185`,
    ##   `kdd2009`.`Var186`,
    ##   `kdd2009`.`Var187`,
    ##   `kdd2009`.`Var188`,
    ##   `kdd2009`.`Var189`,
    ##   `kdd2009`.`Var190`,
    ##   `kdd2009`.`Var191`,
    ##   `kdd2009`.`Var192`,
    ##   `kdd2009`.`Var193`,
    ##   `kdd2009`.`Var194`,
    ##   `kdd2009`.`Var195`,
    ##   `kdd2009`.`Var196`,
    ##   `kdd2009`.`Var197`,
    ##   `kdd2009`.`Var198`,
    ##   `kdd2009`.`Var199`,
    ##   `kdd2009`.`Var200`,
    ##   `kdd2009`.`Var201`,
    ##   `kdd2009`.`Var202`,
    ##   `kdd2009`.`Var203`,
    ##   `kdd2009`.`Var204`,
    ##   `kdd2009`.`Var205`,
    ##   `kdd2009`.`Var206`,
    ##   `kdd2009`.`Var207`,
    ##   `kdd2009`.`Var208`,
    ##   `kdd2009`.`Var209`,
    ##   `kdd2009`.`Var210`,
    ##   `kdd2009`.`Var211`,
    ##   `kdd2009`.`Var212`,
    ##   `kdd2009`.`Var213`,
    ##   `kdd2009`.`Var214`,
    ##   `kdd2009`.`Var215`,
    ##   `kdd2009`.`Var216`,
    ##   `kdd2009`.`Var217`,
    ##   `kdd2009`.`Var218`,
    ##   `kdd2009`.`Var219`,
    ##   `kdd2009`.`Var220`,
    ##   `kdd2009`.`Var221`,
    ##   `kdd2009`.`Var222`,
    ##   `kdd2009`.`Var223`,
    ##   `kdd2009`.`Var224`,
    ##   `kdd2009`.`Var225`,
    ##   `kdd2009`.`Var226`,
    ##   `kdd2009`.`Var227`,
    ##   `kdd2009`.`Var228`,
    ##   `kdd2009`.`Var229`,
    ##   `kdd2009`.`Var230`,
    ##   `kdd2009`.`churn`
    ##  FROM
    ##   `kdd2009`
    ##  ) tsql_55954727470555473770_0000000000

``` r
d <- materialize(db, d, table_name = tmp_name_gen())

y_name <- "churn"
vars <- setdiff(column_names(d), c(y_name, "sample_col"))

d_train <- d %.>%
  select_rows_nse(., sample_col <= 0.5) %.>%
  materialize(db, ., table_name = tmp_name_gen())

d_test <- d %.>%
  select_rows_nse(., sample_col > 0.9) %.>%
  materialize(db, ., table_name = tmp_name_gen())

d_variable_design <- d %.>%
  select_rows_nse(., (sample_col > 0.5) & (sample_col <= 0.9)) %.>%
  materialize(db, ., table_name = tmp_name_gen())
```

``` r
cl = parallel::makeCluster(4)
print(length(vars))
```

    ## [1] 230

``` r
# treat variables in small groups to manage memory
vgroups <- split(vars, ceiling(seq_len(length(vars))/10))
treatment_plans <- lapply(vgroups,
                          function(vi) {
                            di <- d_variable_design %.>%
                              select_columns(., c(y_name, vi)) %.>%
                              execute(db, .)
                            vtreat::designTreatmentsC(di, vi, y_name, 1, 
                                                      parallelCluster = cl,
                                                      verbose = FALSE)
                          })
n_new <- vapply(treatment_plans,
                function(tpi) {
                  nrow(tpi$scoreFrame)
                }, numeric(1))
n_new <- sum(n_new)
approximate_df <- length(vars) + n_new
theshold <- 1/(1 + approximate_df)
# try to get Bonferroni- corrected valid derived variables.
newvars <- lapply(treatment_plans,
                  function(tpi) {
                    sfi <- tpi$scoreFrame
                    sfi$varName[(sfi$sig < theshold) & 
                                   (sfi$rsq >= 1.0e-3)]
                  })
newvars <- unlist(newvars)
print(length(newvars))
```

    ## [1] 129

``` r
rqplan <- as_rquery_plan(treatment_plans, var_restriction = newvars)
```

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var192'(character,character)->character->'Var192_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var193'(character,character)->character->'Var193_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var194'(character,character)->character->'Var194_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var195'(character,character)->character->'Var195_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var196'(character,character)->character->'Var196_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var197'(character,character)->character->'Var197_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var198'(character,character)->character->'Var198_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var199'(character,character)->character->'Var199_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var200'(character,character)->character->'Var200_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var201'(character,character)->character->'Var201_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var202'(character,character)->character->'Var202_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var203'(character,character)->character->'Var203_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var204'(character,character)->character->'Var204_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var205'(character,character)->character->'Var205_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var206'(character,character)->character->'Var206_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var207'(character,character)->character->'Var207_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var208'(character,character)->character->'Var208_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var210'(character,character)->character->'Var210_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var212'(character,character)->character->'Var212_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var214'(character,character)->character->'Var214_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var216'(character,character)->character->'Var216_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var217'(character,character)->character->'Var217_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var218'(character,character)->character->'Var218_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var219'(character,character)->character->'Var219_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var220'(character,character)->character->'Var220_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var221'(character,character)->character->'Var221_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var222'(character,character)->character->'Var222_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var223'(character,character)->character->'Var223_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var225'(character,character)->character->'Var225_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var226'(character,character)->character->'Var226_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var227'(character,character)->character->'Var227_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var228'(character,character)->character->'Var228_catP') , class
    ## vtreatment

    ## Warning in as_rquery.vtreatment(ti, var_restriction = var_restriction):
    ## vtreat::as_rquery not yet implemented for vtreat 'Prevalence
    ## Code'('Var229'(character,character)->character->'Var229_catP') , class
    ## vtreatment

``` r
# ops <- flatten_fn_list(d_train, rqplan$optree_generators)
# cat(format(ops))
# sql <- to_sql(ops, db)
d_train <- materialize_treated(db, rqplan, d_train, 
                               tmp_name_gen(), 
                               temporary = TRUE, overwrite = TRUE)
length(column_names(d_train))
```

    ## [1] 107

``` r
cdata::qlook(db, d_train$table_name)
```

    ## table `kddvtreat_21842353247301301133_0000000004` spark_connection spark_shell_connection DBIConnection 
    ##  nrow: 24951 
    ##  NOTE: "obs" below is count of sample, not number of rows of data.
    ## 'data.frame':    10 obs. of  107 variables:
    ##  $ churn                           : int  -1 -1 -1 -1 -1 -1 -1 -1 -1 -1
    ##  $ Var112_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var113_clean                    : num  33657 90994 168554 21927 -38397 ...
    ##  $ Var119_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var123_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var125_clean                    : num  3060 7020 16650 4869 189765 ...
    ##  $ Var125_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var126_clean                    : num  6 -0.835 -22 -0.835 -26 ...
    ##  $ Var126_isBAD                    : int  0 1 0 1 0 0 0 0 0 1
    ##  $ Var13_clean                     : num  2136 648 720 2112 2968 ...
    ##  $ Var13_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var132_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var133_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var134_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var140_clean                    : num  5810 1350 805 185 11845 ...
    ##  $ Var140_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var143_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var144_clean                    : num  9 9 9 0 36 18 18 18 9 18
    ##  $ Var144_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var153_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var160_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var163_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var173_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var181_isBAD                    : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var189_clean                    : num  269 269 269 246 354 ...
    ##  $ Var193_catB                     : num  -0.431 0.138 0.138 0.138 -0.445 ...
    ##  $ Var193_lev_x_2Knk1KF            : int  0 0 0 0 1 1 0 1 1 1
    ##  $ Var193_lev_x_RO12               : int  0 1 1 1 0 0 1 0 0 0
    ##  $ Var195_lev_x_taul               : int  1 1 1 1 1 1 1 1 1 1
    ##  $ Var198_lev_x_fhk21Ss            : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var200_lev_x_NA                 : int  0 0 1 0 0 0 0 0 0 0
    ##  $ Var202_catB                     : num  0.847 0.942 -8.738 -0.667 -8.605 ...
    ##  $ Var204_lev_x_z5Ry               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var205_catB                     : num  -0.0989 -0.0989 0.6806 -0.0989 -0.0926 ...
    ##  $ Var205_lev_x_sJzTlal            : int  0 0 1 0 0 0 0 0 0 0
    ##  $ Var205_lev_x_VpdQ               : int  0 0 0 0 1 1 1 0 1 0
    ##  $ Var206_catB                     : num  -0.0527 0.0666 0.0666 0.0666 -0.3973 ...
    ##  $ Var206_lev_x_hAFG               : int  0 0 0 0 0 0 0 0 0 1
    ##  $ Var206_lev_x_haYg               : int  0 0 0 0 0 0 0 1 0 0
    ##  $ Var206_lev_x_IYzP               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var206_lev_x_NA                 : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var206_lev_x_y6dw               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var206_lev_x_zm5i               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var207_catB                     : num  -0.531 -0.292 0.112 0.112 0.112 ...
    ##  $ Var207_lev_x_7M47J5GA0pTYIFxg5uy: int  1 0 0 0 0 0 0 0 0 0
    ##  $ Var207_lev_x_me75fM6ugJ         : int  0 0 1 1 1 1 1 1 1 1
    ##  $ Var21_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var210_catB                     : num  -0.0518 -0.0518 -0.0518 -0.0518 -0.0518 ...
    ##  $ Var210_lev_x_g5HH               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var210_lev_x_uKAI               : int  1 1 1 1 1 1 1 1 1 1
    ##  $ Var211_lev_x_L84s               : int  1 1 0 1 1 0 1 1 1 1
    ##  $ Var211_lev_x_Mtgm               : int  0 0 1 0 0 1 0 0 0 0
    ##  $ Var212_catB                     : num  -10.348 -0.347 0.212 0.212 0.212 ...
    ##  $ Var212_lev_x_NhsEn4L            : int  0 0 1 1 1 0 0 0 0 0
    ##  $ Var212_lev_x_XfqtO3UdzaXh_      : int  0 0 0 0 0 1 1 1 1 1
    ##  $ Var214_lev_x_NA                 : int  0 0 1 0 0 0 0 0 0 0
    ##  $ Var216_catB                     : num  -6.659 0.0876 1.0474 0.0666 -0.1373 ...
    ##  $ Var216_lev_x_XTbPUYD            : int  0 0 0 0 0 1 0 0 0 0
    ##  $ Var217_catB                     : num  0.847 -6.659 -8.738 -0.282 -8.605 ...
    ##  $ Var218_catB                     : num  0.132 -0.233 0.132 0.132 0.132 ...
    ##  $ Var218_lev_x_cJvF               : int  0 1 0 0 0 1 0 0 1 1
    ##  $ Var218_lev_x_UYBR               : int  1 0 1 1 1 0 1 1 0 0
    ##  $ Var22_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var220_lev_x_4UxGlow            : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var221_catB                     : num  -0.5489 -0.355 0.0888 0.0888 0.0888 ...
    ##  $ Var221_lev_x_oslk               : int  0 0 1 1 1 1 1 1 1 1
    ##  $ Var221_lev_x_zCkv               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var222_lev_x_catzS2D            : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var225_catB                     : num  -0.0486 -0.3488 0.1621 -0.0486 -0.0486 ...
    ##  $ Var225_lev_x_ELof               : int  0 1 0 0 0 1 0 0 0 0
    ##  $ Var225_lev_x_NA                 : int  0 0 1 0 0 0 0 0 0 0
    ##  $ Var226_catB                     : num  -0.172 -0.2 -0.192 -0.2 0.273 ...
    ##  $ Var226_lev_x_7P5s               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var226_lev_x_FSa2               : int  0 0 0 0 1 0 0 0 0 0
    ##  $ Var227_catB                     : num  -0.294 -0.225 0.111 0.111 0.111 ...
    ##  $ Var227_lev_x_RAYp               : int  0 0 1 1 1 1 1 1 1 1
    ##  $ Var227_lev_x_ZI9m               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var228_lev_x_55YFVY9            : int  0 0 0 0 1 1 0 1 0 0
    ##  $ Var228_lev_x_F2FyR07IdsN7I      : int  0 1 1 1 0 0 1 0 0 0
    ##  $ Var228_lev_x_ib5G6X1eUxUn6      : int  1 0 0 0 0 0 0 0 0 0
    ##  $ Var228_lev_x_iyHGyLCEkQ         : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var228_lev_x_TCU50_Yjmm6GIBZ0lL_: int  0 0 0 0 0 0 0 0 1 1
    ##  $ Var229_catB                     : num  0.154 0.154 0.154 0.154 0.154 ...
    ##  $ Var229_lev_x_am7c               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var229_lev_x_mj86               : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var229_lev_x_NA                 : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var25_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var28_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var35_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var38_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var44_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var6_clean                      : num  1897 966 1162 574 1589 ...
    ##  $ Var6_isBAD                      : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var65_clean                     : num  9 18 9 9 9 9 9 9 27 27
    ##  $ Var65_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var7_clean                      : num  7 14 7 7 7 7 7 7 21 14
    ##  $ Var7_isBAD                      : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var72_clean                     : num  4.2 3 3 3 3 ...
    ##  $ Var73_clean                     : num  126 84 90 100 126 118 92 126 166 160
    ##  $ Var74_clean                     : num  203 35 224 140 490 7 0 28 175 21
    ##  $ Var74_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var76_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var78_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var81_clean                     : num  8520 181203 94249 4808 115048 ...
    ##  $ Var81_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var83_isBAD                     : int  0 0 0 0 0 0 0 0 0 0
    ##  $ Var85_isBAD                     : int  0 0 0 0 0 0 0 0 0 0