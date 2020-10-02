# AppleWatchWorkoutAnalysis
A data analysis from my health app data to highlight the results of my workouts

- Tools used for the project: Python, Pandas, Anaconda, Jupyter, Data Studio, Health App on iPhone

Steps:
  1. Exported data from my Apple Device: Used the Health App and exported as an XML file
  
  2. Used Jupyter Notebooks to read the XML file: import package xmltodict
  
  3. For my analysis I only used the workout data to create my dataframe: 
  workouts_list = input_data['HealthData']['Workout'] 
  df_workouts = pd.DataFrame(workouts_list)
  
  4. I converted some of the columns to numeric form for proper calculations:
  df_workouts[["@duration", "@totalDistance", "@totalEnergyBurned"]] = df_workouts[["@duration", "@totalDistance", "@totalEnergyBurned"]].apply(pd.to_numeric)
  df_workouts.dtypes
  
  5. Then I converted the date formatting:
  format = '%Y-%m-%d %H:%M:%S %z'
  
  6. I only selected a few columns(1-12) for my data analysis:
  df_workouts = df_workouts.iloc[:,0:12]
  
  7. Renamed the activity types:
  df_workouts["@workoutActivityType"]= df_workouts["@workoutActivityType"].replace("HKWorkoutActivityTypeCycling", "Cycling")
  
  8. Exported as a CSV file
  
  9. I chose to use Google Data Studio as my visualization tool and created a pie chart with my top 4 workouts and the breakdown of each workout based on record count, total energy burned(kcal), and the duration. This is referenced in the Apple_Workout_Analysis.pdf document. 
