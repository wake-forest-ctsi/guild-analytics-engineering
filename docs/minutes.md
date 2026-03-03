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