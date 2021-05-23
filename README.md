# ipl-dashboard-test
Step1 ( First Commit ): Setup Spring boot Project : Check README.md
	
	Spring initizlier:
		Java: 9
		Group Id: com.onlypankaj
		ArtifactId: ipl-dashboard
		Project-Type: maven
		Packaging: Jar
		ProjectName: ipl-dashboard
		Project Description: ipl-dashboard test
		Package Name: com.onlypankaj
	
	
	Dependency:
		Devtools
		Web
		HyperSQL Database
		Spring Batch
		Spring JPA
		
	Run the code
		
Step2: Initialize Database to Read csv file : Check README.md

	a. Add match-data.csv to resources
	b. Go to Link for sample Spring batch 
		Google search: spring batch load csv file
		Go to link: https://spring.io/guides/gs/batch-processing/
	c. Spring Batch: 
		Create a Business Class: 
			data:MatchInput to receive csv file as is.
			model:Match to transfer MatchInput to DB and map to DB
		Create an Intermediate Processor:
			data: MatchDataProcessor implements ItemProcessor, input MatchInput and write to Match
					MethodImplement:process input MatchInput and output to Match
			Add logic to store team1 as first batted team and team2 as vice versa based on toss decision
			
			Run the code
		Put Together a Batch Job:
			date: BatchConfig with @Configuration @EnableBatchProcessing
				Factory: JobBuilderFactory, StepBuilderFactory
				Create 3 methods:
					reader()
					processor()
					writer(DataSource dataSource)
					
				Create 2 process
					Job
					Step
					
					Make Match as Entity
					
				Add JobCompletionNotificationListener
					afterJob
					
Step3: Prepare additional aggregated data: Team
		
		a. Add model:team with summary of team matches won and played
		b. Upload data to team via JobCompletionNotificationListener:afterJob
			Create a blank HashMap of String(TeamName) and Team
			Union is not supported by JPA so call query twise and update the list.
		c. Display team data after upload
		
			
			
				
					
					
					
	
	
