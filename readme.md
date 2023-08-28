Sample file for Jenkis demo
## Chain Jobs
Create Jobs -> go to specific job -> configure ->post build ->build other project ->choose ->save
make this chain for others as well

Manage -> Pugins ->Build pipeline(install) -> 

Dashboard -> + -> Build Pipeline view -> Name -> Select Initial Job -> No Of Displayed Builds -> No ->Save 

 * Yellow = in progress
 * Blue = Yet to be done
 * Green = executed

![demo](https://github.com/OliGanguly/Jenkis-Demo/assets/82031303/b42d600f-0c0e-4994-8905-691e371c1bef)

## Jenkis Pipeline
* Pipeline = [Dev -> Application Test -> Integration Test -> Acceptance Test -> Production]
  we have a pipeline here all the jobs/ processes are linked with each other , That is one runs after the other
  they all executed with a automatic trigger . so id dev job is successfull it automatically runs test job and so on..
 * Jenkis Pipeline - I s a Way to implement ci cd , all jobs starting from Build to deploye to test to release can be chained with each other .
 * JenkinsFile - To implement Jenkins Pipeline we use jenkins file, is a pipeline as a code.[Write Script ]
  ## Steps
   Step 1 : Start Jenkins

   Step 2 : Install Pipeline Plugin [Manage -> Pulgin]

   Step 3 : Create A New Job Name it type should be Pipeline

   Step 4 : PipeLine Section

            PipeLine Script -> Declerative Format  -> Write Code -> Apply ->Save

   Step 5 : Build Now

   ![JenkinsPipeline](https://github.com/OliGanguly/Jenkis-Demo/assets/82031303/f38e12d6-d08a-4bd6-85b8-756a91f8154d)

             


