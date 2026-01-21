Here’s the agent-aware version of the flow: 

1️⃣ PRD Creation 

/agent tpo.agent 
/prd.of.feature 

2️⃣ QA PRD Review (before code) 

/agent qa.agent 
/qa.prd.review 

➡️ PRD updated / confirmed 

3️⃣ Implementation 

/agent dev.agent 
/prd.to.implementation 


4️⃣ Ralph Review 

/agent dev.agent 
/ralph.auto.pipeline 



5️⃣ QA Validation 

/qa.test.scenarios 
/qa.exploratory.testing 
/qa.regression.gate 

6️⃣ PR Review 

/reviewer.agent 
/ralph.final-gate 