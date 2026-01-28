When working with a data migration story theirs 2 aspects that should be configured before running the program;
- ***TempGroundDisturbanceIds*** => these are the IDs you will be fetching from Arcs
- ***DataMigrationWithTempGroundDisturbanceIds*** => setting this to true, enables the application to include temporary ground disturbance IDs during the data migration process. This might be necessary if the migration involves handling or processing data related to these IDs, which are defined in the TempGroundDisturbanceIds list in your code. If these IDs are critical for the migration, you should set this value to true
	- ![[Pasted image 20250624143037.png]] 
- Once that is done user can run the Data Migration project that will wipe the existing ARs in your local then import the ARCs, ARs into your local DB 
- Note to self: if an AR cannot be migrated into LAMS, the plausibility is that the ARs has been Declined thus we do not migrate it into LAMS
	- ![[Pasted image 20250624143547.png]]
The migration process in the `DataMigrationBase` class operates as follows:

1. **Initialization**:
   - The class is initialized with source and target database contexts (`SourceDbContext` and `TargetDbContext`), an `IMapper` instance for mapping entities, and a logger for logging errors or information.

2. **Migration Settings**:
   - Various migration settings are defined, such as `IncludeAllVersions`, `IncludeApprovalRequestHistories`, and `IsUsingTempGroundDisturbance`, which control the behavior of the migration process.

3. **Run Migration**:
   - The `RunMigrationAsync` method determines whether the migration should run in batches or as a single operation based on the `_isBatch` flag.
   - If `_isBatch` is `true`, it calls `RunMigrationByBatchesAsync`. Otherwise, it calls `RunMigrationSingleAsync`.

4. **Batch Migration**:
   - In `RunMigrationByBatchesAsync`, records are fetched from the source database in chunks (defined by `fetchRecordCount`).
   - Each batch of records is mapped to target entities using `MapRecords`.
   - The mapped records are saved to the target database using `SaveTargetRecordsAsync`.
   - This process repeats until all records are processed.

5. **Single Migration**:
   - In `RunMigrationSingleAsync`, all source records are fetched at once.
   - The records are mapped to target entities using `MapRecords`.
   - The mapped records are saved to the target database using `SaveTargetRecordsAsync`.

6. **Mapping Records**:
   - The `MapRecords` method iterates through the source records.
   - It checks for duplicate records using `IsDuplicateRecord`. If a record is a duplicate, it is skipped.
   - Each source record is mapped to a target record using `MapRecord`.
   - If `IncludeAllVersions` is enabled, amendment records are mapped using `MapAmendmentRecords` and stored in `amendmentEntities`.

7. **Saving Records**:
   - The `SaveTargetRecordsAsync` method adds each target record to the target database context.
   - Changes are saved in batches to optimize performance.

8. **Updating Records**:
   - The `UpdateTargetRecordsAsync` method updates existing records in the target database based on amendment data.
   - It uses `MapAmendmentToSourceRecord` to map amendment data to the source record.

9. **Amendment Cycle Migration**:
   - The `RunAmendmentCycleMigrationAsync` method processes amendment records in cycles based on the `amendmentEntities` dictionary.

10. **Error Handling**:
    - Errors during migration are logged using the `Logger` instance, and exceptions are rethrown for further handling.

This process ensures that data is migrated efficiently and accurately, with support for batch processing, duplicate record handling, and amendment updates.


## Utility Class - for classes without a DI container 
- The reason why we use `IConfigurationRoot configuration = ConfigurationBuilderHelper.Get();` instead of injecting `Iconfiguration` is due to the DataMigration Project being standalone thus bypassing the DI setup and instead utilizing a helper class to build and return the configuration file once and reused for subsequent calls
- Static helpers provide quick, global access to configuration without needing to pass dependencies through constructors or method parameters.
- This approach is common in migration or utility projects where full DI setup is unnecessary or adds complexity.

```
internal static IConfigurationRoot Get()  
{  
    return _configuration ??= new ConfigurationBuilder()  
        .SetBasePath(Directory.GetCurrentDirectory())  
        .AddJsonFile(Constants.ConfigurationFileName)  
        .Build();  
}
```


1. Configuration and Initialization
The migration process starts in Program.cs, which sets up configuration (from appsettings.json), logging, and dependency injection.
Services, repositories, and migration classes are registered for use throughout the migration.
2. Loading Migration Settings
The application reads migration settings and parameters from appsettings.json or command-line arguments.
These settings determine which migrations to run, source/target database connections, and any feature flags (e.g., DataMigrationWithTempGroundDisturbanceIds).
3. Preparing Data Sources
The migration classes (e.g., BusinessUnitMigration.cs, ProjectMigration.cs, SiteMigration.cs) connect to the source data repositories.
Data sources may include SQL databases, CSV files, or other structured data (see the ImportFiles/ and CSV/ folders).
4. Mapping and Transformation
Data is read from the source and mapped to target models using AutoMapper (configured in ConfigureAutoMapper.cs).
Mapping profiles in MappingProfiles/ define how source fields are transformed to target fields, including any necessary data cleaning or normalization.
5. Migration Execution
The main migration logic is orchestrated by MigrationProcess.cs, which calls individual migration classes in sequence.
Each migration class:
Reads source data.
Transforms and validates the data.
Writes the data to the target system (database, files, etc.).
Logs progress and errors using AppLogger.cs.
6. Error Handling and Logging
Errors encountered during migration are logged and, depending on severity, may halt the process or be recorded for review.
Detailed logs are written to files or output, as configured.
7. Reporting and Validation
After migration, reports are generated (see Reports/), summarizing migrated records, errors, and any skipped items.
Validation steps may compare source and target data to ensure integrity.
8. Extensibility
The migration framework is modular: new migration classes can be added for new data types.
Helper utilities in Helpers/ and extension methods in Extensions/ support common tasks.
<hr></hr>
Summary Table of Key Files:
File/Folder
Purpose
Program.cs
Entry point, configures services
appsettings.json
Migration settings and connection strings
MigrationProcess.cs
Orchestrates migration steps
BusinessUnitMigration.cs
Migrates business unit data
ProjectMigration.cs
Migrates project data
SiteMigration.cs
Migrates site data
ConfigureAutoMapper.cs
Sets up data mapping profiles
AppLogger.cs
Handles logging
Reports/
Stores migration reports
Helpers/, Extensions/
Utility functions
ImportFiles/, CSV/
Source data files
<hr></hr>