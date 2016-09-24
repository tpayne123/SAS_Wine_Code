# SAS_Wine_Code
	libname Mydata '/home/SAS_Data' access=readonly;
	libname Mydata1 '/home';
 
 
	****************************************************************************************:
	*  EDA;
	****************************************************************************************;

	proc contents data=mydata.wine;
	run;

	proc print data=mydata.wine(obs=10);
	run;

	proc means data=mydata.wine(drop=INDEX) nmiss mean min p5 median  mode P95 max stddev ndec=3;
	run;

	proc freq data=mydata.wine(drop=INDEX )  ;
   	tables target labelappeal acidindex stars /   missing;
	run;

	proc sgplot data=mydata.wine;
  		vbox target;
  		xaxis label='Cases';
  		keylegend / title="Box Plot";
	run;

	proc univariate data=mydata.wine noprint;
  	histogram target/vscale=count normal midpoints= 0 1 2 3 4 5 6 7 8;
	run;

	*//Fixed Acidity;
	proc sgplot data=mydata.wine;
  		vbox FixedAcidity / category=target;
  		xaxis label='Cases';
  		keylegend / title="Box Plot";
	run;

	proc univariate data=mydata.wine noprint;
  	histogram FixedAcidity/vscale=count;
	run;

	proc genmod data=mydata.wine;
	 model target= fixedacidity / dist=poi link=log;
	run;

	*//Volatile Acidity;
	proc sgplot data=mydata.wine;
	  vbox VolatileAcidity / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;

	proc univariate data=mydata.wine noprint;
	 histogram VolatileAcidity/vscale=count;
	run;

	proc genmod data=mydata.wine;
	   model target= VolatileAcidity / dist=poi link=log;
	run;
	
	*//Citric Acid;
	proc sgplot data=mydata.wine;
	  vbox CitricAcid / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram CitricAcid/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= CitricAcid / dist=poi link=log;
	run;
	
	*//Residual Sugar;
	proc sgplot data=mydata.wine;
	  vbox ResidualSugar / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram ResidualSugar/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= ResidualSugar / dist=poi link=log;
	run;
	
	*//Chlorides;
	proc sgplot data=mydata.wine;
	  vbox Chlorides / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram Chlorides/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= Chlorides / dist=poi link=log;
	run;
	
	*//Free Sulfur Dioxide;
	proc sgplot data=mydata.wine;
	  vbox FreeSulfurDioxide / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram FreeSulfurDioxide/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= FreeSulfurDioxide / dist=poi link=log;
	run;
	
	*//Total Sulfur Dioxide;
	proc sgplot data=mydata.wine;
	  vbox TotalSulfurDioxide / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram TotalSulfurDioxide/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= TotalSulfurDioxide / dist=poi link=log;
	run;
	
	*//Density;
	proc sgplot data=mydata.wine;
	  vbox Density / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram Density/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= Density / dist=poi link=log;
	run;
	
	*//pH;
	proc sgplot data=mydata.wine;
	  vbox ph / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram ph/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= ph / dist=poi link=log;
	run;
	
	*//Sulphates;
	proc sgplot data=mydata.wine;
	  vbox Sulphates / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram Sulphates/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= Sulphates / dist=poi link=log;
	run;
	
	*//Alcohol;
	proc sgplot data=mydata.wine;
	  vbox Alcohol / category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc univariate data=mydata.wine noprint;
	  histogram Alcohol/vscale=count;
	run;
	
	proc genmod data=mydata.wine;
	   model target= Alcohol / dist=poi link=log;
	run;
	
	*//Label Appeal;
	proc sgplot data=mydata.wine;
	  vbox LabelAppeal/ category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc freq data=mydata.wine;
	    table  labelappeal / missing plots(only)=freqplot;
	run;
	 
	  
	proc genmod data=mydata.wine;
	   model target= LabelAppeal / dist=poi link=log;
	run;
	
	*//Acid Index;
	proc sgplot data=mydata.wine;
	  vbox AcidIndex/ category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc freq data=mydata.wine;
	    table  AcidIndex / missing plots(only)=freqplot;
	run;
	 
	proc genmod data=mydata.wine;
	   model target= AcidIndex / dist=poi link=log;
	run;
	
	*//STARS;
	proc sgplot data=mydata.wine;
	  vbox stars/ category=target;
	  xaxis label='Cases';
	  keylegend / title="Box Plot";
	run;
	
	proc freq data=mydata.wine;
	    table  stars / plots(only)=freqplot;
	run;
	 
	proc genmod data=mydata.wine;
	   model target= stars / dist=poi link=log;
	run;
	
	****************************************************************************************:
	* Data Prep;
	****************************************************************************************;
	
	*///fix missing values define new vars etc///;
	
	data testdata;
	   set mydata.wine;
	   fixedacidity_A=abs(fixedacidity);
	   volatileacidity_A=abs(volatileacidity);
	   citricacid_A=abs(citricacid);
	   ResidualSugar_a=abs(ResidualSugar);
	   chlorides_A=abs(chlorides);
	   FreeSulfurDioxide_A=abs(FreeSulfurDioxide);
	   TotalSulfurDioxide_A=abs(TotalSulfurDioxide);
	   Sulphates_A=abs(Sulphates);
	   alcohol_A=abs(alcohol);
	
	   ph_A=ph;
	   if ph_A<2 then ph_A=3.208;
	run;
	
	data testdata2;
	   set testdata;
	   if residualsugar_A = "." then residualsugar_a = 5.419;
	   if chlorides_A = "." then chlorides_a = 0.055;
	   if freesulfurdioxide_A = "." then freesulfurdioxide_a = 30.846;
	   if totalsulfurdioxide_A = "." then totalsulfurdioxide_a = 120.714;
	   if ph_a = "." then ph_a = 3.208;
	   if sulphates_a = "." then sulphates_a = 0.527;
	   if alcohol_a = "." then alcohol_a = 10.489;
	   
	   stars_a= stars;
	   stars_m =0;
	   if stars = "." then do;
	       stars_A = 2; 
	       stars_m=1;
	   end;
	   
	   taste=ResidualSugar_A* CitricAcid_A;
	run;   
	   
	
	proc means data=testdata2 (drop=INDEX) nmiss mean median max min ndec=3;
	run;
	
	****************************************************************************************:
	* Model 1 Poisson;
	****************************************************************************************; 
	proc genmod data=testdata2;
	  model target=volatileacidity_A TotalSulfurDioxide_A alcohol_A LabelAppeal AcidIndex stars_a 
	    stars_m/ dist=poisson link=log;
	  output out=test1 pred=count resdev=dev1;
	  store out=poimodel;
	run;
	
	proc gplot data=test1;
	   plot dev1*count;
	run;
	
	proc plm source=poimodel;
	        score data=testdata2 out=payne_wine_poi pred=p_target_poi/ ilink;
	run;
	
	data mydata1.payne_wine_poi;
	   set payne_wine_poi;
	   p_target_poi=round(p_target_poi,1);
	   keep index p_target_poi;
	run;
	
	****************************************************************************************:
	* Model 2 NB;
	****************************************************************************************; 
	
	proc genmod data=testdata2;
	   model target=  volatileacidity_A TotalSulfurDioxide_A alcohol_A LabelAppeal
	                  AcidIndex stars_a stars_m/ dist=nb link=log  ;
	   store out=nbmodel ;
	run;
	
	proc plm source=nbmodel;
	        score data=testdata2 out=payne_wine_nb pred=p_target_nb   / ilink;
	run;
	
	*///create the file in a saved library for your results///;
	data mydata1.payne_wine_nb;
	   set payne_wine_nb;
	   p_target_nb= round(p_target_nb,1);
	   keep index p_target_nb;
	run;
	
	****************************************************************************************:
	* Model 3 ZIP;
	****************************************************************************************; 
	
	proc genmod data=testdata2 ;
	   model target= Alcohol_A LabelAppeal AcidIndex Stars_A Stars_M /  dist=zip link=log;
	   
	   zeromodel Volatileacidity_A TotalSulfurDioxide_A pH_A Sulphates_A Alcohol_A 
	             LabelAppeal AcidIndex Stars_A Stars_M /link=logit;    
	   store out=zipmodel;
	run;
	
	proc plm source=zipmodel;
	        score data=testdata2 out=trng_payne_wine pred=p_target_zip pzero=P_ZERO_ZIP/ ilink;
	run;
	
	data trng;
	   set trng_payne_wine;
	   proc sort  ;
	   by p_zero_zip  ;
	   run;
	   
	
	proc plm source=zipmodel;
	        score data=testdata2 out=payne_wine_zip pred=p_target_zip pzero=P_ZERO_ZIP/ ilink;
	run;
	 
	data mydata1.payne_wine_zip_zero;
	   set payne_wine_zip;
	   if p_zero_zip>.38 then p_target_zip = 0;
	   p_target_zip=round(p_target_zip);
	   keep index p_target_zip p_zero_zip;
	run;
	
	proc print data=mydata1.payne_wine_zip_zero(obs=10);
	run;
	
	proc freq data=mydata1.payne_wine_zip_zero;
	   tables p_target_zip;
	   run;
	
	****************************************************************************************:
	* Model 4 ZINB;
	****************************************************************************************; 
	
	proc genmod data=testdata2;
	   model target= Alcohol_A LabelAppeal AcidIndex stars_a stars_m / dist=zinb link=log;
	       
	   zeromodel volatileacidity_A TotalSulfurDioxide_A ph_A Sulphates_A alcohol_A LabelAppeal
	             AcidIndex stars_a stars_m /link=logit;
	   store out=zinbmodel;
	run;
	
	proc plm source=zinbmodel;
	        score data=testdata2 out=payne_wine_zinb pred=p_target_zinb pzero=p_zero_zinb/ ilink;
	run;
	
	data payne_wine_zinb;
	   set payne_wine_zinb;
	   proc sort  ;
	   by p_zero_zinb;
	run;
	   
	
	proc plm source=zinbmodel;
	        score data=testdata2 out=payne_wine_zinb pred=p_target_zinb pzero=P_ZERO_ZInb/ ilink;
	run;
	 
	data mydata1.payne_wine_zinb_zero;
	   set payne_wine_zinb;
	   if p_zero_zinb>.38 then p_target_zinb= 0;
	   p_target_zinb=round(p_target_zinb);
	   keep index p_target_zinb p_zero_zinb;
	run;
	
	proc print data=mydata1.payne_wine_zinb_zero(obs=10);
	run;
	
	proc freq data=mydata1.payne_wine_zinb_zero;
	   tables p_target_zinb;
	   run;
	
	****************************************************************************************:
	* Model 5 OLS;
	****************************************************************************************; 
	
	*///regression model is left for you to do the next dataset is for demo///;
	proc reg data=testdata2 outest=betas plots=diagnostics(stats=(default aic));
	model TARGET =  FixedAcidity VolatileAcidity CitricAcid 
	Taste fixedacidity_A volatileacidity_A citricacid_A ResidualSugar_a
	chlorides_A FreeSulfurDioxide_A TotalSulfurDioxide_A Density ph_A Sulphates_A
	alcohol_A LabelAppeal AcidIndex stars_a stars_m
	/ selection=stepwise slentry=.01 slstay=.01 ;
	run;
	quit;
	
	proc score data=testdata2 score=betas
	   out=mydata1.payne_wine_reg type=parms;
	   var  VolatileAcidity Volatileacidity_A TotalSulfurDioxide_A Alcohol_A
	        LabelAppeal AcidIndex Stars_A Stars_M;
	run;
	
	data mydata1.payne_wine_reg;
	      set mydata1.payne_wine_reg;
	      p_target_reg = round(MODEL1);
	      keep index  p_target_reg;
	run;
	
	****************************************************************************************:
	*Selection;
	****************************************************************************************; 
	*///merge all of the model results together///;
	
	data payne_wine_all;
	merge mydata1.payne_wine_poi(in=ina) mydata1.payne_wine_nb(in=inb) 
	   mydata1.payne_wine_zip_zero mydata1.payne_wine_zinb_zero mydata1.payne_wine_reg mydata.wine;
	by INDEX;
	if ina;
	run; 
	
	data mydata1.payne_wine_all;
	   set payne_wine_all;
	   keep index target p_target_poi p_target_nb p_target_zip p_target_zinb p_target_reg;
	run;
	
	proc print;
	run;   
	
	%macro FIND_ERROR( DATAFILE, P, MEANVAL );
	
	%let ERRFILE 	= ERRFILE;
	%let MEANFILE	= MEANFILE;
	
	data &ERRFILE.;
	set &DATAFILE.;
		ERROR_MEAN	= abs( target - &MEANVAL.)	**&P.;
		ERROR_POI		= abs( target - P_TARGET_POI )	**&P.;
		ERROR_NB		= abs( target- P_TARGET_NB )	**&P.;
		ERROR_ZIP		= abs( target - P_TARGET_ZIP )	**&P.;
		ERROR_ZINB	= abs( target - P_TARGET_ZINB )	**&P.;
		ERROR_REG	= abs( target - P_TARGET_REG )	**&P.;
	run;
	
	
	proc means data=&ERRFILE. noprint;
	output out=&MEANFILE.
		mean(ERROR_MEAN)	=	ERROR_MEAN
		mean(ERROR_POI)	=	ERROR_POI
		mean(ERROR_NB)	=	ERROR_NB
		mean(ERROR_ZIP)	=	ERROR_ZIP
		mean(ERROR_ZINB)	=	ERROR_ZINB
		mean(ERROR_REG)	=	ERROR_REG
		;
	run;
	
	data &MEANFILE.;
	length P 8.;
	set &MEANFILE.;
		P		= &P.;
		ERROR_MEAN	= ERROR_MEAN	** (1.0/&P.);
		ERROR_POI 	= ERROR_POI	** (1.0/&P.);
		ERROR_NB 		= ERROR_NB	** (1.0/&P.);
		ERROR_ZIP 	= ERROR_ZIP	** (1.0/&P.);
		ERROR_ZINB 	= ERROR_ZINB	** (1.0/&P.);
		ERROR_REG 	= ERROR_REG	** (1.0/&P.);
		drop _TYPE_;
	run;
	
	proc print data=&MEANFILE.;
	run;
	
	%mend;
	
	*//A value of 1 will give the AVERAGE ERROR
	A value of 2 will give the ROOT MEAN SQUARE ERROR
	A value of some other constant, say 1.5, will use that exponent;
	
	
	%FIND_ERROR( payne_wine_all, 1, 3 );
	%FIND_ERROR( payne_wine_all, 1.5, 3 );
	%FIND_ERROR( payne_wine_all, 2, 3 );
		
	proc contents data=mydata.wine_test;
	run;
	   
	
	****************************************************************************************:
	*data step;
	****************************************************************************************; 
	
	data traindata;
	   set mydata.wine_test;
	   
	   fixedacidity_A=abs(fixedacidity);
	   volatileacidity_A=abs(volatileacidity);
	   citricacid_A=abs(citricacid);
	   ResidualSugar_a=abs(ResidualSugar);
	   chlorides_A=abs(chlorides);
	   FreeSulfurDioxide_A=abs(FreeSulfurDioxide);
	   TotalSulfurDioxide_A=abs(TotalSulfurDioxide);
	   Sulphates_A=abs(Sulphates);
	   alcohol_A=abs(alcohol);
	
	   ph_A=ph;
	   if ph_A<2 then ph_A=3.208;
	   
	   if residualsugar_A = "." then residualsugar_a = 5.419;
	   if chlorides_A = "." then chlorides_a = 0.055;
	   if freesulfurdioxide_A = "." then freesulfurdioxide_a = 30.846;
	   if totalsulfurdioxide_A = "." then totalsulfurdioxide_a = 120.714;
	   if ph_a = "." then ph_a = 3.208;
	   if sulphates_a = "." then sulphates_a = 0.527;
	   if alcohol_a = "." then alcohol_a = 10.489;
	   
	   stars_a= stars;
	   stars_m =0;
	   if stars = "." then do;
	       stars_A = 2; 
	       stars_m=1;
	   end;
	   
	   taste=ResidualSugar_A* CitricAcid_A;
	
	run; 
	
	data mydata1.payne_wine_final;
	set traindata;
	TEMP = 1.1723 
	       + 0.0072*Alcohol_A 
	       + 0.2323*LabelAppeal 
	       - 0.02*AcidIndex 
	       + 0.105*Stars_A 
	       - 0.1829*Stars_M;
	P_SCORE_ZIP_ALL = exp( TEMP );
	
	TEMP =  -2.2815
	        + 0.2121*Volatileacidity_A 
	        - 0.0011*TotalSulfurDioxide_A 
	        + 0.1985*pH_A 
	        + 0.1819*Sulphates_A 
	        + 0.0280*Alcohol_A 
	        + 0.7206*LabelAppeal 
	        + 0.4319*AcidIndex 
	        - 3.8077*Stars_A 
	        + 5.8783*Stars_M;
	P_SCORE_ZERO = exp(TEMP)/(1+exp(TEMP));
	
	P_Target=round(P_SCORE_ZIP_ALL);
	if P_SCORE_ZERO > .38 then P_Target=0;
	
	Keep index p_target;
	run;
	
