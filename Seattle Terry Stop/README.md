<h1 align="center"> Seattle Terry Stop Data </h1> <br>
<p align="center">
  <a href="https://github.com/bryan-md/Seattle-Terry-Stops">
    <img alt="Seattle Terry Stop Data" title="Seattle Terry Stop Data" src="https://imgur.com/l5PJvRj.png">
  </a>
</p>
<p align="center"> Are There Racial Biases In Terry Stops In Seattle, WA?
</p>
<h3>Background:</h3>

<p>There has been a rise in tension between law enforcement and the public. I've seen & read many news articles with a lot of rhetoric. As a new Seattleite, I was interested in determining if there was a racial bias with law enforcement and race in the city of Seattle. I decided to to look into Terry Stops performed in the City of Seattle, and come to my own conclusion. </br></p>

<p>Through Seattle's <a href="https://data.seattle.gov/">Open Data Program</a>, I was able to download the <a href="https://data.seattle.gov/Public-Safety/Terry-Stops/28ny-9ts8">Terry Stop Data</a> from the past few years, perform statistical and exploratory analysis on the data, with the goal of creating a model that would predict the race of a subject that had been stopped by an officer. Can this prediction be made only by the demographic information of both the officer and subject?</p>

<h3> Key Findings:</h3>
<ul style="list-style-type:circle;">
  <li>White residents make up 51% of Terry Stops, and are 66% of Seattle's population</li>
  <li>Black residents are the second most stopped group, accounting for 31% of stops, making up 8% of the Seattle population</li>
  <li>Black residents are stopped 300 times more than the Seattle 2010 census population proportions reported, all other captured races were stopped below the 2010 census proportions</li>
  <li>Black & Multi-Racial residents had the highest percentage of the juvenile (1-17) population stopped at 8% & 7.7% respectivley(p<.05)</li>
  <li>Native Alaskans aged 36 and over have the highest percentage of stops (p<.05)</li>
    <li>White residents are not Frisked and arrested at the same proportions of Non-White residents (p<.05). White residents are stopped the most, however, they have the lowest frisk rate among all races at 18% (p<.05)</li>
  <li>The analysis includes 3 interactive plots visualizing the Terry Data</li>
  <li>Four predictive models were created to predict a stopped subjects race with varying amounts of demographic data, neighborhood information and/or a police officer's unique id.</li>
  <li>While there is significant findings in a difference in Terry Stops & Frisks among races, the models were not able to accurately predict the race of a subject (or frisk) with only officer demographic data.</li>
</ul>

<h3> Overview:</h3></br>
<p>There is a difference between one police officer stopping one individual, which is a tactical definition, and systematic promotion of this tactic on either the departmental or municipal level, which can damage police–community trust and lead to charges of racial profiling.</br> 

**What is a Terry Stop?**
</br>
Under the 1968 Terry v. Ohio ruling , a police officer may stop and detain a person based on reasonable suspicion . And, if the police reasonably suspect the person is armed and dangerous, they may also frisk him or her for weapons.
A stop is justified if the suspect is exhibiting any combination of the following behaviors:

- Appears not to fit the time or place.
- Matches the description on a "Wanted" flyer.
- Acts strangely, or is emotional, angry, fearful, or intoxicated.
- Loitering, or looking for something.
- Running away or engaging in furtive movements.
- Present in a crime scene area.
- Present in a high-crime area (not sufficient by itself or with loitering).

**What is a Frisk?**</br>
A frisk is a type of search that requires a lawful stop. It involves contact or patting of the person's outer clothing to detect if a concealed weapon is being carried. The frisk doesn't necessarily always follow a stop. The law of frisk is based on the "experienced police officer" standard whereby an officer's experience makes him more equipped to read into criminal behavior than the average layperson.
The purpose of a frisk is to dispel suspicions of danger to the officer and other persons. The frisk should only be used to detect concealed weapons or contraband. If other evidence, such as a suspected drug container, can be felt under the suspect's clothing, it can be seized by the officer. 

A frisk is justified under the following circumstances:

- Concern for the safety of the officer or of others.
- Suspicion the suspect is armed and dangerous.
- Suspicion the suspect is about to commit a crime where a weapon is commonly used.
- Officer is alone and backup has not arrived.
- Number of suspects and their physical size.
- Behavior, emotional state, and/or look of suspects.
- Suspect gave evasive answers during the initial stop.
- Time of day and/or geographical surroundings (not sufficient by themselves to justify frisk).

A stop requires Reasonable Suspicsion, a set of factual circumstances that would lead a reasonable police officer to believe criminal activity is occurring. A Frisk is based on the 'experienced policed officer'. A few of the above behaviors can be subjective. From the Exploratory Data Analysis, we found that Subjects stopped of White race were 'frisked ' at a much lower rate than all the other races. 

There is a difference between one police officer stopping one individual, which is a tactical definition, and systematic promotion of this tactic on either the departmental or municipal level, which can damage police–community trust and lead to charges of racial profiling.

The goal is to investigate the Terry Stops in Seattle by race of the subject and officer, and gain insight if the percentage of stops match the demographic of the city. Also, to help identify if certain officers have a higher prevalence of stops of a certain race. 

<h3>Statistical Analysis</h3>
<p>Was conducted using bootstrop analysis among proportions</p>

<h3> Data Wrangling & EDA</h3>
<p>Was conducted using Seaborn, Matplotlib, Pandas, Numpy, & Bokeh</p>

<h3> Model Construction</h3>
<p>Most of the models created were multi class classification. The models were created with Logistic Regression, Random Forest, KNeighbors & SVC Classifiers (binary) for their accuracy, training time or multi-class implementation.

One Vs. Rest Classifier was chosen because of the multi class scenario. To be able to easily provide a set of probabilities for each reace. </p>

<h4>Preprocessing pipelines</h4>
<ul style="list-style-type:circle;">
  <li><b>Synthetic Minority Over-sampling Technique (SMOTE)</b> was utilized due to imbalanced data over the 6 classes. SMOTE was utilized to resample the minority classes during the pipeline.</li>
  <li><b>imbalaned-Pipeline</b> was utilized because of the imbalanced dataset. This allowed for resampling during the pipeline process</li>
  <li><b>Standard Scaler</b> was utilized to scale the data</li>
  <li><b>GridSearchCV</b> was utilized to perform a 5 fold cross validation over the selected parameters for each classifier.</li>
  <li><b>Test-Train-Split</b> was utilized to set aside the test set, with a 20% test size.</li>
</ul>

<h4>Performance metrics</h4>
<ul style="list-style-type:circle;">
  <li><b>Log loss</b> was utilized for the multi class problem. This metric is better utilized than accuracy for the imbalance seen in the data. Along with evaluation of precision, recall & accuracy from the confusion matrix & classification report, to help visualize & interpret the performance of the data</li>
  <li><b>Accuracy score</b> was utilized for the binary model.</li>

</ul>


<h3>Use:</h3>
<ul style="list-style-type:circle;">
  <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/1%20-%20Data%20Wrangling.ipynb">1 -Data Wrangling</a>Explores and cleans the source data</li>
  <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/2%20-%2001%20Data%20Story%20Telling%20Exploratory%20Analysis.ipynb">2 - 01 Data Story Telling Exploratory Analysis</a>Visually Explores features in the datasets and distributions.</li>
  <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/2%20-%2002%20Data%20Visualization.ipynb">2 - 02 Data Visualization</a>Interactive Bokeh plots. These notebooks need to be downloaded and run locally to view. See the preview below</li>
  <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/3%20-%20Inferential%20Statistics.ipynb">3 - Inferential Statistics</a>Statistical hypothesis testing to test differences among populations via bootstrapping</li>
  <li><b>Machine Learning Models</b> - production of the following pipelines with slightly different features and/or target variable.</li>
      <ul>
        <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/4%20-%2001%20ML-Officer%20and%20Subject%20Demographics.ipynb">4 - 01 ML-Officer and Subject Demographics</a></li>
         <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/4%20-%2002%20ML%20-%20Officer%20Demographics.ipynb">4 - 02 ML - Officer Demographics</a></li>
        <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/4%20-%2003%20-%20ML%20-%20Officer%20and%20Additional%20Features.ipynb">4 - 03 - ML - Officer and Additional Features</a></li>
        <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/4%20-%2004%20-%20ML%20Frisk.ipynb">4 - 04 - ML Frisk</a>(binary model)</li>
      </ul>
 <li><a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/notebooks/05%20-%20Subject%20Race%20Prediction.ipynb">5 - Subject Race Prediction</a>The second model was placed in a function for the user to input a few parameters and display prediction probabilities for the race of the subject that was stopped.</li>
</ul>
</p>


<h2 align = "center">Bokeh Plots</h2>
<p align = "center">These plots need to be ran locally to see/interact with them</p>
<ul style="list-style:none;">
  <li><img src="https://i.imgur.com/5ZhfYAX.gif" alt="Bokeh Plot 1"></br><p align = "center">This plot visualizes trends above/below the census demographic population proportions for the selected race</p></li>
  <li><img alt="Bokeh Plot 2" src="https://i.imgur.com/m9kncKn.png"><p align = "center">This plot displays a comparison between a selected race of  PD officers vs 'non' selected race PD officers and the distrubtion of subject stops for the selected month</p> </li>
  <li><img alt="Bokeh Plot 3" src="https://i.imgur.com/hlaIdgL.gif"><p align = "center">This plot compares the difference in distributions between two types of races of officers and a selected subject race</li></p>
</ul>

<h2 align = "center">Subject Race Prediction</h2>
<p align = "center">This program takes three paramaters. The Officer ID, the initial call type, and the 'beat' and returns a dataframe with the probability predictions for the subjects race. <a href="https://github.com/bryan-md/Seattle-Terry-Stops/blob/master/PARAMETER%20CODES.txt">A list of all parameters can be found in the parameter text document</a>. </br>
  <ul style="list-style: none;">
    <li><b>Officer ID:</b>the unique id for the officers </li>
    <li><b>Initial Call Type:</b> the type of call that initiated the stop (all stops were limited to officer initiated stops). </li>
    <li><b>Beat</b> Where the stop occured.</li>
    <li><code align = "center">predict_subject_race (457, 40, 'E2' )</code></li>
    <li><p >Returns a Pandas DataFrame of race probability predictions</br><img align="center" src="https://i.imgur.com/qgQJZAQ.png" alt="Bokeh Plot 1"></li>
  </ul>
</p>
