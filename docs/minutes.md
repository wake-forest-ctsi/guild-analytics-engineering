## 5th August 2025 - Guild Kickoff 🧙‍♂️

- Michael introduced the purpose of the guild and reviewed the [charter](./charter.md):
    - **Goal**: Turn our discussions in this guild into documentation about what we should be doing as analytics engineers
	- We have a [GitHub repository](https://github.com/wake-forest-ctsi/guild-analytics-engineering) for the guild, which utilizes MkDocs to keep track of guild documentation
	- We have a Teams channel for quick discussions, and can have longer-term discussions in the Discussions tab on the guild's GitHub page
	- Upcoming guild meetings will be in the calendar on the guild's Teams channel
    - Archivist role will act as an editor in organizing guild content and documentation, currently assigned to Irina
- The guild will be referred to as the "Analytics Engineering Guild", but we also have a whimsical name (MAGES) and a fun logo! Any feedback is welcome regarding the name of the guild.
- Anyone is welcome to be a member! Just let Michael know and he'll add you to the guild's Teams channel.
- Guild will tentatively continue meeting at 3 PM EST on Tuesdays, but this is not set in stone. Contact Michael if you have any scheduling issues.
- Vote in the poll in the Teams channel on what topics you'd like to discuss
	- If you have any other topic ideas, please add them to the [list of ideas](./schedule.md/#other-topic-ideas)!
- The hope is that people will use the guild's Teams channel to ask questions and connect with peers so we can work together to find solutions

## 3rd March 2026 - dbt Fusion ⚡

- Michael reviewed the purpose of the guild, as laid out in the [charter](./charter.md):
	- The group agreed that Tuesdays at 3pm is a good time for the guild to meet. The goal is meet once a month.
	- 📢 We're asking for volunteers to present on a topic, whether from the [list of potential topics](./schedule.md#other-topic-ideas), or on a topic that you'd like to share with the group!
	- The guild meeting is also intended to provide an opportunity for attendees to discuss their work and any questions/issues they're facing.
	- 👉 We highly encourage guild members to post in the guild's Teams channel. This way, everyone can provide help/input, and you don't need to wait until the next meeting to discuss an issue. 
- Michael presented about [dbt Fusion](https://docs.getdbt.com/docs/fusion/about-fusion):
	- **Introduction:** Fusion is dbt's new interpreter and uses a Rust backend (rather than Python), making it faster than dbt Core. It brings a lot of cool features and is friendly to use. For example, Fusion allows you to:
		- Preview your dataset within VSCode, rather than needing to jump back and forth between Snowflake (This is limited to 1000 rows by default, but can be changed in your VSCode preferences)
		- View lineage graphs for columns and tables (similar to the DAG produced by dbt docs, but nicer)
		- Leverage code completion
	- **Getting Started:**
		- Install the [dbt extension](https://marketplace.visualstudio.com/items?itemName=dbtLabsInc.dbt) in VSCode, and **please ensure you're downloading the extension authored by dbt Labs Inc**
		- Once you have the extension installed, you will need to set up some configuration:
			- Check for Fusion compatability - Essentially checking to ensure that there are no deprecation issues and your code meets dbt's structure expectations (especially surrounding tests)
			- Select "no" when asked if you have a cloud account
			- Select "yes" when asked if you have an existing project
			- Your project will then be parsed and static analysis will be performed
			- If the above completes successfully, you should be able to use Fusion right away within your project! If not, you should be prompted to install the auto fix to re-structure your project
		- Notes:
			- You need to register within 15 days
			- As well as the extension, this also installs LSP (the interpreter)
	- **Practical Demonstration:** Michael used dbt's example jaffle shop project to demonstrate the features of Fusion:
		- Fusion allows you to quickly change your target (e.g. switch from running in dev to prod)
		- With Fusion, you don't have to have Python installed to run dbt since it runs in its own Rust virtual environment
		- Use `dbtf` to ensure you're using the Fusion version of dbt, though the command `dbt` will fall back on the Fusion version if you don't have Python installed
		- In the top right of VSCode, you'll notice a shortcut button to open a command window with all the different dbt commands you can run (e.g., run a model, run a model and all of its parents, test a model, etc.)
		- In the top right of VSCode, you'll notice a "Compile File" shortcut button to generate the SQL for your model, so you no longer need to go digging through the target folder
		- Fusion provides a cleaner summary of the models and tests that are running
		- If you right-click and rename a model, Fusion will automatically update the name of all the references to that model within other model files
	- **Limitations of Fusion:**
		- Fusion doesn't generate docs
		- Fusion doesn't yet work with duckdb
		- When a model is renamed, Fusion doesn't update the name of the model in yml files (i.e., tests, documentation)
- Michael opened up the floor to discuss [possible upcoming guild presentation topics](./schedule.md#other-topic-ideas) and asked for topic ideas and volunteers
	- If you are interested in presenting, please let Michael know and he can get you scheduled!
	- Members requested the following topics:
		- dbt tags / dependency selection to be able to run an individual set of models
		- Best use case for tags and how we should use them
		- Sample feature in dbt
		- The heavier topics from the below table so we can do things right the first time as we build our codebases 

			Topic | Votes
			--- | ---
			Data Modeling Splash | ?
			Data Modeling DASH | 3
			Snowflake | 4
			Duckdb | 2
			Data Modeling - I2B2 | 3
			DBT Fusion | ?
			Data Modeling - OMOP | 4
			How to work with data engineers | 0
			How to work with analysts | 0
			Naming and why it matters | 3
			Testing your models | 1
			Environments: Dev vs Production | 5
			Automation | 3
			Data model ownership and sharing responsibility across verticals | 1
			Data modeling - dimensional modeling | 

## 8th May 2026 - Machine Learning and Data Models 🧭

- 📜 Michael opened the meeting with a reminder to the guild that we have a Codex where we keep track of the learning we get from guild meetings, along with the meeting minutes collected by the Archivist. 
	- This Codex may eventually be moved to SharePoint rather than MkDocs. 😢

- 🎤 Michael opened the floor to general questions or for attendees to share any interesting things they've learned recently.
	- Alex shared that he has found dbt's [persist_docs](https://docs.getdbt.com/reference/resource-configs/persist_docs?version=1.12) to be very useful. By adding the following lines to your `dbt_project.yml` file, the table and column descriptions you have in your model yaml files will be visible in Snowflake.  
		```yaml
		models:
		  <resource_path>:
			+persist_docs:
			  relation: true
			  columns: true
		```

- 👉 Michael asked attendees to let him know if there are other teammates who we think should be in the guild so that they can join as well.
	- 📆 If you would like to be a permament member of the guild, let Michael know! He will add you to the Teams channel so you can get notified of upcoming meetings.

- 🎥 *Recording started*: Zhitu presented on his experiences and challenges using machine learning against some of the big data models we have&mdash;the Research Data Mart and PCORNet. The slides are available on the guild's Teams channel.
	- **Three Essential Pieces in an ML Model**:
		1. The *input*, `x`, such as a PCORNet table, image, or text
		2. The *model*, such as regression, random forest, or an LLM
		3. The *output*, `y`, such as an image or score
	- **Definitions**:
		- *Training (fine tuning)*: Given `x` and `y`, figure out the model
		- *Inference*: Given `x` and the model, figure out `y`
	- **Overview of Steps**:
		- Define problem `y`
		- Find `x`, that is, collect and clean data---*This is the most important piece!*
		- Do the ML---*This is less than 10% of the total effort*
		- Evaluate the model
		- Deploy and monitor
	- **Example**: Zhitu showed the postpartum depression project as an example
		- For this project, the target variable `y` is either 0 or 1 for whether the mother developed postpartum depression
		- Since this isn't a field in the PCORNet model, they needed to use phenotyping to define `y`
			- Upshot: There are different methods for constructing the target variable. He found that how `y` is defined is *critical* and even more important that which model you use. The result can vary greatly depending on how `y` is defined.
	- **When defining the problem...**
		- Zhitu shared an important lesson he learned in the case of the admission data. It was only towards the end of the work that he discovered that the label indicating whether a student received an interview was randomized based on the interview pool, meaning it can't be predicted!
		- For the data request chatbot project, he and the team spent a lot of time learning about what the needs of the project are and how success should be defined and measured. These are good questions to ask when beginning ML work.
		- For the deidentified notes projects, important questions to ask were what the level of accuracy should be and what the expected performance (speed) requirements are. These evolve along the way and inform the model.
	- **When collecting and cleaning up the data...**
		- The AMMI (postpartum depression) project used PCORNet, while the Splash project used the admission data
		- Zhitu found that pairing up with a data engineer turned out to be critical! It's difficult to find the data yourself, so having a data engineer to work with is very helpful.
		- Michael asked (and discussion ensued): If there's no data engineer, what makes a good model?
			- Something like PCORNet is good. There are just a few tables and you can look up ICD10 or LOINC codes, and there's a lot of documentation
			- The Splash project was difficult because we didn't have the same level of documentation and were figuring it out as we went, with limited access to the data owners
			- Ideally, ML programmers would never need to go back to data owners  for clarification, but the question is how do we build a data model that achieves this
	- **Unresolved problems**:
		- Messy data, e.g., LOINC lab results 
			- Found some data in PCORNet was mapped incorrectly since the unit is not consistent (so it's not the same measurement)
			- The result of a lab is sometimes text, so he needed to figure out how to normalize between results like "neg" and "negative" or fix typos like "feww"
		- Should data cleaning happen upstream at the database or downstream by the researcher or somewhere in between?
			- Michael chimed in that researchers should define the data elements and their values. Then, either you have data that maps exactly, or you map unmatched data to "Other" and store the raw value somewhere. The responsibility lands on analytics engineer to try to figure out the mapping or to go to a subject expert if needed. 
		- We need to save all data and document transforms from one place to another but how do we do that in reality? There's no clear solution.
		- Something that may be obvious by eye, e.g., unit conversion, may be hard at scale
		- Missing data, e.g. Splash essay scores
	- **When evaluating the model...**
		- Once you have `x` and `y`, how do you ensure the model runs okay?
			- A good fit (ideal) model captures the pattern but doesnt fit all the points
			- Overfitting means the model learns the noise, so the model fits nearly every point but it ends up being very complex
			- In practice, the data is split into training and validation. Then, the model fits the training data but the validation on unseen data checks the generalization. This helps build a model that doesn't overfit
		- Another challenge is doing a formal validation, which Zhitu explained using the data request chat bot as an example:
			- The chat bot answers are not repeatable, so to test, the team created fake researchers and evaluated the bot
			- They want the chat bot to output the same thing each time but this doesn't always happen
			- Zhitu thanked the PM team for keeping track of how data requests evolve. Having this info is how the team is now able to evaluate the chat bot, so it's important to keep all this info!
			- Vishnu asked: How are chat bot responses are evaluated?
				- The team evaluated the final chat bot output with the ground truth. It doesn't need to be exact
	- **When deploying and monitoring...**
		- Tradeoff between using the HPC for fine tuning (which needs a lot of data) and inference versus using Snowflake API calls for inference using the best LLM model in Snowflake (but no fine tuning). The former is free but the latter costs money
		- There's the challenge that the database itself keeps changing but a snapshot of all data at that point is needed for training to be able to fine tune the model. This will create a conflict later on when the model is in production
	- Finally, Zhitu shared his favorite resources for learning ML. Please refer to the last slide of the presentation in Teams to find these useful resources!
	
- 👏 Thank you Zhitu for a great presentation! The guild had a great discussion after the presentation. Here are some of the highlights, but please refer to the recording for the full discussion.
	- Michael asked: How do you get the results of the ML model back into the data model?
		- Reference the model and weight and metadata in Snowflake for the inference and then write that back into Snowflake
		- For Splash, write raw scores back to table in an ML output table. This then becomes a source for our dbt models. Ideally the whole process (dbt + ML) would run from start to end, but we have to break in the middle to run the ML part outside of building the data model. We don't have a good way to orchestrate this yet
		- Alex mentioned that in Snowflake, it's possible to call ML functions directly in SQL and wondered if we could leverage this in dbt. Michael replied that this is something we could try, but this is costly so we aren't yet running everything on Snowflake.
	- Vishnu asked: In any ML models that we developed so far, did we see any cases where a model performed well at the time but then degraded afterwards when new data was included? 
		- For the deidentified notes project, the training set consists of several years of data. For new data, Zhitu noticed that computer names are different and these got missed by the model, so he did see a drift in performance if the underlying data is many years apart. 
		- For the postpartum depression project, inference on the data didnt change very much since the data covered multiple years.
	- Ginny asked: For the Splash project, how do past essays get saved? Where are the raw scores being populated from? 
		- They are stored in ML analysis schema. Zhitu only ran only this once in November when the admission cycle was completed. If we wanted to do this weekly during the admission cycle, we would want to ensure that we only perform the computation for new data that comes in and append to the table, since it's costly to run on the full data (a few hundred dollars for 10k essays). Michael mentioned this can be achieved by an incremental build
	- Michael asked: In the AMMI project, how did you start with PCORNet data and end up with a feature model? What were the issues with long versus wide rows?
		- For the ML model, the input `x` is one row, e.g., one patient or one delivery. The columns are features, e.g, age or time of delivery. The PCORNet model doesn't look like this, so Zhitu used dbt to transform the raw PCORNet data into format needed for the ML model.
		- This resulted in thousands of columns, which is too wide for SQL Server to handle. Zhitu had to store the data in a long table, then pivot the data in pandas before feeding it into the ML model. Luckily, Snowflake shouldn't have this issue and we can have as many columns as we want. 
		- Michael mentioned that there's value in getting a feature model from data model that is already clean and fixed so that there's no need for extra transformations for the ML programmers to do. 
	- Kanika asked: In the Splash project, how were the seven values scored and what did the model look like?
		- The admission committee supplied the definitions for each of the values. Zhitu used a Llama model to score the essays based on the criteria. 
	- Alex asked: In the Splash project, was the inference for each of the seven values done individually (run seven times) or was there one inference run that computed all seven scores?
		- There were seven individual runs, one for each value. Zhitu found that the performance was better this way.

- 📢 Michael asked for volunteers for the next presentation. You can choose from the list of possible topics that people are interested in (see the topics from the last meeting's minutes) or present on another topic that interests you! 
	- This doesn't need to be a huge presentation, just a couple of slides and a discussion
	- Please reach out to Michael if you'd like to present!

## 19 August 2026 - OMOP Data Model 🌀

- 🎥 *Recording started*: Michael opened up the meeting, and indicated he hopes to increase the frequency of guild meetings to once a month.

- 🎤 Michael then opened the floor to general analytics questions or to any topics people wanted to share.
	- Emmanuel and David had related questions about how to work with PHI in dbt and whether it could be stored in seed files.
		- Michael responded that PHI should not be kept in seed files. Instead, the data should be stored in a file on SharePoint, and the data engineers can then load it into a raw schema in the database. This way, there's no chance of that PHI data getting uploaded to GitHub. (Michael also mentioned that we probably should have a common SharePoint folder to store data, which is something Karina may be working on.)
		- Ginny mentioned that Alex has an existing process to load data from SharePoint into a raw schema so you can connect with him if you have questions. She also mentioned that if you need a short-term solution so you can work with the data to build your models, you can temporarily upload the file into your personal schema. Then, once the data has been loaded into the raw schema by the data engineers, you can switch schemas in your code.
		- Alex mentioned that his current setup will periodically check for new files if you set a mode to check for files in a subfolder path, so you don't need to ask every time you drop a file (useful if you're doing this often).
		- Michael also pointed out that we will need to deal with this a lot in the future, since every data request in SharePoint will have a folder where the requester can upload files with PHI, and we will need this data in Snowflake when working on fulfilling data requests.

- 🌀 Next, Emmanuel presented on how he and the team have been building up the OMOP data model from our Clarity systems.
	- OMOP (Observational Medical Outcomes Partnership) is from OHDSI, which is an open science community spanning academia, industry, and government with a goal of improving patient care.
	- **The problem**: No two systems store data in the same way (not even our own two Epic instances!) so a query that works in one database may break in another.
	- **The solution**: The [OMOP Common Data Model](https://ohdsi.github.io/CommonDataModel/)! Once data is transformed into this standard form, it can run on any database.
		- There's a great overview of the six areas in which tables are grouped in the CDM if you follow the link above.
	- Emmanuel walked us through *concepts*, *domains*, and the *source to concept map*. 
		- *Concepts* are a unit of clinical meaning to which a unique ID is assigned, called the concept ID. 
		- Each concept belongs to a *domain* and these domains do not overlap.
		- We have data in our source system that we have to represent in OMOP, but the data in our Clarity instance will like differ from that in the Clarity instances at other sites, so we have to represent our source data in a standard format in order for it to be used at other sites. This is where the *source to concept map* comes into play.
			- Emmanuel showed us an example in Athena, OMOP's concept browser, and explained that non-standard concepts need to be translated to a vocabulary that is standard in OMOP, like SNOMED codes.
	- Emmanuel highlighted the portions of data domains we currently have mapped in our OMOP system, so please refer to the slides to see those!
	- Emmanuel then delved deeper into the dbt code.
		- He explained that because we're working with two Clarity systems (SE and AAH), they have a macro that unions both data together, allowing us to have one staging model that can be used everywhere. However, you can use the MDP source column if you need to restrict which site you want data from.
		- He also explained that in these staging models, they also try to filter data before using it. For example, the patient model filters patients based on service area, whether they're a valid patient, etc.
		- He pointed out the documention, done using [dbt doc blocks](https://docs.getdbt.com/docs/build/documentation?version=2) (allowing you to write your documentation in markdown and pass that to the yaml when running `dbt docs generate`), which contains information about models as well as the key decisions taken to build the model.
			- Ginny asked if this documentation is hosted anywhere. Michael responded that first we need infrastructure from Will, and then we will host the documentation.
		- He also showed the custom tests that have been created and which are reusable across models.

- 👏 Thank you Emmanuel for a great presentation! The guild had some great Q&A and discussion after the presention. Highlights are below, but please refer to the recording for more details!
	- Michael asked how we can keep any modifications we may need to make to the data model in step with the documentation. He proposed that we could just rely on the dbt docs to show the different columns, or we could bring in the OMOP docs as they're generated and modify those.
	- Michael asked Emmanuel what his biggest worries currently are with converting data to the OMOP CDM.
		- Emmanuel responded that the biggest challenge is the mapping process and putting things into the source to concept map. He highlighted flowsheets as an example. We already have some flowsheets linked to LOINC codes, which can then be linked to OMOP concepts, but we still have many flowsheets in our system that don't have any standard concepts attached to them.
			- Additonally, flowsheets sometimes contains vitals, PHQs, and differences in data types, so this variety makes it difficult to put all the data into one model.
			- David also pointed out that the data volumes involved with flowsheets are also huge
		- Emmanuel also mentioned that they have encountered cases where there are differences between the southeast and the midwest since data is stored in different tables across different systems. In general, these cases are easy to fix with queries, for example having two separate intermediate queries for patient ethnic background.
			- Michael suggested that instead of two intermediate models, we could have one model and join to both of the tables the two systems are using. Since, theoretically, the values in one of the tables will be null, we could do a coalesce. Then the code should still work if one system moves data to the other table. 
	- Michael asked if there are any parts of the dbt code they'd like to go back and fix, given that they've learned a lot since starting this effort a year ago. 
		- Emmanuel responded that to start with, in order to make things easeer, they've broken things up into similar groups and unioned them together, but in future it might be possible to merge these queries together. This should help speed up the run time for the long run, as well as keep logic consistent (since if you need to change logic in one model, you need to make sure you change it in the other, related models).
	- Emmanuel asked about the logistics of creating incremental models in dbt since currently the source date isn't propagated from staging to intermediate models.
		- Michael said the source date would need to be brought forward into the intermediate data. When you join models, you'll need to check the maximum of the new dates. If that is newer than the previous maximum, you know you may have new data in the row that needs to be updated/inserted. If not, then you don't need to do anything, so you save a lot of time with not doing as many inserts or updates (which is the goal of using incremental models).
			- Michael also pointed out that there is a way in Snowflake to do this all for "free" where we don't have to do the work. This is by leveraging dynamic tables, and Snowflake tracks what's changed in metadata, so downstream tables can be updated based on that metadata rather than column data. However, our Snowflake currently isn't set up for this feature.

- 📢 Michael asked that if people have any ideas for topics (skills, tools, models, or projects) that they want to learn more about in the guild meetings, please post your suggestion in the guild's Teams channel!
	- He would appreciate volunteers to present on topics, otherwise he may reach out to people.
	- Since the guild roles are meant to be rotated between members, Irina also motioned to pass the baton to a new Archivist. 🫡

- 🧋 The guild also had a "water cooler" discussion at the end of the meeting.
	- Irina mentioned how she's been enjoying using [uv](https://docs.astral.sh/uv/), which led to some discussion about using uv with dbt.

		> Irina's basic workflow using uv:
		>
		>- `uv init` : Run this inside the root folder of the project to create the virtual environment (you only need to run this once)
		>
		> - `uv add <package_name>` :  Install a dependency inside the virtual environment
		>
		> - `uv run <command>` : Run any command within the virtual environment, e.g., `uv run python main.py`, `uv run dbt build ...`, etc.
		>
		> - `uv sync` : Recreates the virtual environment based on the toml and lock files (useful if you've deleted the virtual environment or are cloning an existing project from GitHub)
		>
		>Other great things:
		>
		> - It creates a toml file and a lock file with your dependencies (and sub-dependencies) and their pinned versions, along with the required python version. These are updated anytime you install new dependencies.
		> 
		> - You just need to prefix any command you run from the CLI with `uv run` and uv will automatically run the code in the virtual environment. (No need to remember to activate the environment first!)
	
	- Alex asked if we can have a guild session targeted towards aligning on our use of uv, dbt, and python, including ensuring everyone is using the same versions.
	- Michael also mentioned that he's a fan of dbt fusion, but they have unfortunately moved the column lineage feature to the paid version (thought there is a similar feature in Snowflake that we can leverage).


