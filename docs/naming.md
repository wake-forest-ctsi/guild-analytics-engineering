

## Why
Practice verbosity in a reproducible way. Extra characters in a name are free. Potential errors caused by choosing the wrong database object or mental complexity as your DAG/project expands to entropy can cost a lot.

Schemas are the most granular point of authorization we can use.  Any user who has access to read/write a table in a schema has access to all tables in that schema.

#  How
We only have a single database available that serves for development, testing, and production.  The general format for a schema name is, <dag_stage>_<source/topic>__<additional_context>, but there is specific guidance for each stage.

### Development
Every development schema needs to have clear ownership.  We accomplish this by having every development schema name begin as <process>_<username>, where process defines the type of work and username is a consistent name that a teammate uses across nexus (preferably their advocatehealth username).

<DBT>_<MHORVATH>

### Raw
The raw schema is where data is landed, with as little modification is possible, from the source system.  This is the domain of the data engineers, who are responsible for ensuring the data from the source systems are available, current, and accurate.

The naming schema allows for specificity, but does not require it.  If there is a single source for human resources data, such as workday, then there only needs to be a schema named RAW_WORKDAY, without a division or hospital system.

Sections need to be consistently used and documented, for example we don't want a source for data from epic clarity to sometimes be called RAW_EPIC_CLARITY and sometimes be called RAW_CLARITY.

<RAW>_<SOURCE>_<DIVISION>_<HOSPITAL_SYSTEM>

SOURCE = [CLARITY, MUSE, WORKDAY, ...]
DIVISION = [AAH, ATRIUM]
HOSPITAL_SYSTEM = [CHARLOTTE, WAKE, NAVICENT, FLOYD_HARBIN, ...]

### Staging
Minimal changes to the raw data happens in the staging layer, column renaming and basic mapping.  As such the naming scheme is largely identical to the Raw schemas.

### Intermediate


### Marts
Visible to analysts and end users.

<MART>_<MODEL>_<DIVISION>

MART_OMOP

### Reporting
Visible to analysts and end users, possibly through BI tools.

<RPT>_<TOPIC>