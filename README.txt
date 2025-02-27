-------------------------
CS685 Assignment 1 ReadMe
-------------------------

1. File List:

Shell scripts and json files:
   1.1	   neighbor-districts-modified.json    Contains list of neighbors of a district
   1.2	   case-generator.sh                   Finds total number of cases for each district in a week/month/overall
   1.3	   edge-generator.sh                   Finds the neighbor of each district and output it in an edge-list format
   1.4	   neighbor-generator.sh               Finds the average and standard deviation of the number of cases in the neighboring districts
   1.5	   state-generator.sh                  Finds the average and standard deviation of the number of cases in all other districts in the state	
   1.6     zscore-generator.sh                 Finds the z-score for every district using separately the neighborhood and the state information
   1.7	   method-spot-generator.sh            Finds the hotspot and coldspot districts per week, per month, and overall
   1.8	   top-generator.sh                    Finds the top-5 hotspot and top-5 coldspot districts using both the neighborhood and state methods
   1.9	   assign1.sh                          Top level script to run the entire assignment

.py program files:
   1.10	   ques2.py
   1.11	   ques3.py
   1.12	   ques4.py
   1.13    ques5.py
   1.14	   ques6.py
   1.15	   ques7.py
   1.16	   ques8.py

Supporting files (Available at https://api.covid19india.org):
   1.17	   data-all.json                      Contains information about daily count of cases in each district
   1.18	   district-wise.csv              

2. Steps to run the program:

   2.1 	Please install python 3.6 (or higher) using:
		$ sudo apt-get install python3.6
   2.2 	Additional python packages needed to be installed:
		pandas - $ pip install pandas
		numpy - $ pip install numpy
   2.3 	To run the program from the top, a separate script is provided. Please run assign1.sh. To run some individual program, please run the shell scripts in the top 		down order as listed in section 1.1 as some programs require supporting files which will be generated by some predecessing program.
		$ ./assign1.sh
   2.4 	To run .py programs, please use:
		$ python3 'filename'.py
   2.5	To view neighbor-districts-modified.json:
		$ cat neighbor-districts-modified.json
   2.6	Dependencies among the programs:
	 2.6.1	edge-generator.sh uses the file: 
		->"mapping.csv" generated by case-generator.sh

	 2.6.2	neighbor-generator.sh uses the files: 
		->"dic_week.json", "dic_month.json", "dic_overall.json", "cases-week.csv", "cases-month.csv" and "cases-overall.csv" generated by case-generator.sh. 
		->"district_neighbors.json" generated by edge-generator.sh

	 2.6.3	state-generator.sh uses the files:
		->"mapping.csv", "dic_month.json", "dic_overall.json","cases-week.csv", "cases-month.csv" and "cases-overall.csv" generated by case-generator.sh

	 2.6.4	zscore-genertor.sh uses the files:
		->"cases-week.csv", "cases-month.csv" and "cases-overall.csv" generated by case-generator.sh
		->"neighbor-week.csv","neighbor-month.csv","neighbor-overall.csv" generated by neighbor-generator.sh
		->"state-week.csv","state-month.csv","state-overall.csv" generated by state-generator.sh

	 2.6.5	method-spot-generator.sh uses the files:
		->"dic_week.json", "dic_month.json", "dic_overall.json", "cases-week.csv", "cases-month.csv" and "cases-overall.csv" generated by case-generator.sh
		->"neighbor-week.csv","neighbor-month.csv","neighbor-overall.csv" generated by neighbor-generator.sh
		->"state-week.csv","state-month.csv","state-overall.csv" generated by state-generator.sh

	 2.6.6	top-generator.sh uses the files:
		->"zscore-week.csv","zscore-month.csv","zscore-overall.csv" generated by zscore-generator.sh

Thank you for reading!
