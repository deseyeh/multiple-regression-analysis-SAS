* below code creates a new data set in mydata.pfarg06_1 
creates a new variables Y, Per2-Per7 ;

data Pfarg06_v1;
set mydata.Pfarg06;
Y = 1000 * (B3 + B4 + B6 + B7 + B8) / A1;
Per2 = A2/A1;
Per3 = A3/A1;
Per4 = A4/A1;
Per5 = A5/A1;
Per6 = A6/A1;
Per7 = A7/A1;
run;
quit;

* Below obtain the sample mean and sample standard deviation for the variables Y, A1 and Per2 to Per7;
proc means data=pfarg06_v1;
var y a1 per2 - per7;
run;
quit;

* Obtain a histogram for the response variable Y ;
proc univariate noprint data= pfarg06_v1;
histogram y/vscale=proportion;
run;
quit;
*Obtains a simple frequency distribution for the factors C1 to C8
To explain why c4 should not be included as an explanatory variable in any regression model for Y;
proc freq data=pfarg06_v1;
tables c1 - c8 /norow nocol nopercent ;
run;
quit;



*2. Question 

*	Below code Creates dummy variable for factor c1
;
data pfarg06_v2;
set pfarg06_v1;
if c1 = 1 then c1_1 = 1; else c1_1 = 0;
if c1 = 2 then c1_2 = 1; else c1_2 = 0;
if c1 = 3 then c1_3 = 1; else c1_3 = 0;
run;
* Below code will fit the response Y, and the explanatory variable c1 -

* Obtain a scatter plot of Studentized Residual against the  Predicted value ( with factor)
* Obtain a scatter plot of Y against the  Predicted value ( with factor)
;
proc reg data= pfarg06_v2;
model  y = c1_1 c1_2 c1_3 c2 c3 c5 - c8 a1 per2 - per7 ;
output out = FITSG p = Pred student = Sresid;
plot y * p. ;
plot Student. * P.;
run;
quit;

*The next part of the program is a proc univariate step
;
Title 'Histogram of Student Residual';
proc univariate data = FITSG noprint;
histogram Sresid/normal(noprint);
qqplot Sresid;
run;
title;
quit;
* Prints the Variables Y Predicted, Standardized Residual;
title1 'Variables Y Predicted, Standardized Residual';
proc print data= FITSG;
var y Pred Sresid;
run;
title;



*Question 3
consider the regression of log(Y) on the respective 
logs of A1 and Per2 to Per7, 
and on the (untransformed) factors C1 to C3, and C5 to C8.

;

data pfarg06_v2;
set pfarg06_v2;
LY=log(Y);
LA1 =log(A1);
LPer2 =log(Per2);
LPer3 =log(Per3);
LPer4 =log(Per4);
LPer5 =log(Per5);
LPer6 =log(Per6);
LPer7 =log(Per7);
label LY= 'log of Y'
	LA1 = 'log of A1'
    LPer2 ='log of Per2'
	LPer3 ='log of Per3'
	LPer4 ='log of Per4'
	LPer5 ='log of Per5'
	LPer6 ='log of Per6'
	LPer7 ='log of Per7'; 
run;
quit;
proc print;
run;
* This obtains the predicted plot of the transformed response variable LY against the transformed explanatory variables LA1 Lper2 - Lper7 
	using Class option for the categorical variables c1 - c3 c5 - c8
	It also obtains the Stdentized Residual 
;
proc reg data= pfarg06_v2;
model  Ly = c1_1 c1_2 c1_3 c2 c3 c5 - c8 La1 Lper2 - Lper7 ;
output out = FITSGL p = Pred student = Sresid;
plot Ly * p. ;
plot Student. * P.;
run;
quit;


*The next part of the program is a proc univariate step
;
Title 'Histogram of Student Residual';
proc univariate data = FITSGL noprint;
histogram Sresid/normal(noprint);
qqplot Sresid;
run;
title;
quit;
* Prints the Variables Y Predicted, Standardized Residual
;
title1 'Variables LY Predicted, Standardized Residual';
proc print data = FITSGL;
var LY Pred Sresid;
run;
title;


*Question 4
Employ a backward elimination procedure to the model in Q3

;

proc reg data= pfarg06_v2;
model  Ly = c1 - c3 c5 - c8 La1 Lper2 - Lper7 
			/selection = backward slstay = 0.05;
run;
quit;

*Question 5
Fit the Model

;
/* using Proc GLM
proc glm data= pfarg06_v2;
class c1 c2 ;
model  Ly = c1 c2 La1 Lper2 Lper3; 
run;
quit;
*/
* using proc reg;
Title 'Fitting the final';
proc reg data= pfarg06_v2;
model  Ly = c1_1 c1_2 c1_3 c2 La1 Lper2 Lper3;
plot  Ly * p.;
plot student. * (p. La1 Lper2 Lper3) ;
*plot Student. * P.;
output out = FITSFM p = Pred student = Sresid;
run;
title;
quit;

*The next part of the program is a proc univariate step
;
Title 'Histogram of Student Residual';
proc univariate data = FITSFM noprint;
histogram Sresid/normal(noprint);
qqplot Sresid;
run;
title;
quit;
* Prints the Variables Y Predicted, Standardized Residual
;
title1 'Variables LY Predicted, Standardized Residual';
proc print data = FITSFM;
var LY Pred Sresid;
run;
title;



*Question 6
Investigating Outliers and influential points
;
/* using Proc GLM with class;
proc glm data= pfarg06_v2;
class c1 c2 ;
model  Ly = c1 c2 La1 Lper2 Lper3 /ss3; 
output out = FITS p = Pred student = Sresid rstudent = Dresid;
run;
quit;

*OR 
 using Proc reg with dummy variables;
*/
proc reg data= pfarg06_v2;
model  Ly = c1_1 c1_2 c1_3 c2 La1 Lper2 Lper3;
output out = FITS p = Pred student = Sresid rstudent = Dresid;
run;
quit;
* the below plots an overlay of the Deleted residual and the Studentized residual against thr predicted value
;
symbol1 v = plus c = black;
symbol2 v = circle c = black;
proc gplot data = FITS;
plot (Sresid Dresid) * Pred / overlay vref = 0;
run;
quit;
symbol v = plus c = black;
*/To identify the potential outliers from their deleted residual  /*/;
proc print data=fits;
var Dresid;
where abs(dresid)>=2;
run;


*/* Initial Screening for Influential Points, Investigating the values of DFFITS (a measure of influence) */
;
proc reg data= pfarg06_v2;
model  Ly = c1_1 c1_2 c1_3 c2 La1 Lper2 Lper3;
output out = INFL1 p = Pred dffits = Dff;
run;
quit;
* below SOrts the output data set in descending order of the absolute DFFITS value, 
placing the observation numbers for this sorted data in the variable index
;
data INFL1; set INFL1;
Adff = abs(Dff);
run;

proc sort data = INFL1;
by descending Adff;
run;

data INFL1; set INFL1;
Index = _N_;
run;
* produces the Pareto graph of the absolute DFFITS values

;
proc gplot data = INFL1;
plot ADff*Index / vref = 0.843 vref = 2;
run;
quit;
* below identifies the observations with highest absolute DFFITS values that stands out;
proc print data = INFL1;
var Pred LY Dff;
where Index <= 6;
run;

proc reg data=INFL1 noprint;
model  Ly = c1_1 c1_2 c1_3 c2 La1 Lper2 Lper3;
output out = INFL2 h = H rstudent = Dresid covratio = C;
run;
quit;

proc print data = INFL2;
var  Dff H Dresid C;
where Index <= 6;
run;

* Using sample correlation and VIF to 
investigate potential collinearities between the possible explanatory variables.;

proc reg data = pfarg06_v2 corr;
model  Ly = c1_1 c1_2 c1_3 c2 La1 Lper2 Lper3 / vif;
run;
quit;

* Q 7
95% confidence interval
;
proc reg data = pfarg06_v2 noprint;
model  Ly = c1_1 c1_2 c1_3 c2 La1 Lper2 Lper3 ;
output out = PRED p = PRED lclm = LowerM uclm = UpperM;
run;
quit;

proc print data = PRED;
var c1_1 c1_2 c1_3 c2 La1 Lper2 Lper3 Ly Pred LowerM UpperM;
run;
* using Proc GLM;
proc glm data = pfarg06_v2 noprint;
class c1 c2;
model  Ly = c1 c2 La1 Lper2 Lper3;
output out = PRED p = PRED lclm = LowerM uclm = UpperM;
run;
quit;
proc print data = PRED;
var c1 c2 La1 Lper2 Lper3 Ly Pred LowerM UpperM;
run;

