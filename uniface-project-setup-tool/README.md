# Project Setup Tool #

Project Setup Tool is a wizard for quickly and easily setting up Uniface projects ready for development. It will:

 * Create folders used by the project that aren't in version control, for example, log folders
 * Create project shortcuts (Launch IDE, Run Project etc)
 * Create assignment files from templates, substituting in values based on the developer's local environment
 * Create a new Tomcat context for the project
 * Import source code
 * Perform an initial compile
 * Import application data

All of these actions are controlled by a project.xml file in the root of the project being setup.

## Dependencies ##
The Project Setup Tool has been written and tested with:

 * Uniface 9.7.01
 * SQLite
 * Meta Tools (0.2-9.7)  - https://github.com/uniface/Development-Tooling/tree/master/uniface-meta-tools

Information about the developer's local environment is detected from the Uniface installation. The tool assumes that this is correct but it can be overridden during the setup steps if necessary.

## Setup ##

 * Download the latest zip from the downloads folder
 * Unzip the download into your local Uniface packages directory. This is where you'll keep all your Uniface tooling. These instructions assume this folder is C:\\UnifacePackages\\
 * You should now have a batch file called ProjectSetup.bat in C:\\UnifacePackages\\ along with a folder called ProjectSetup.
 * So that we can invoke the batch file from any where add C:\\UnifacePackages\\ to your path
 * This batch file and the shortcuts that the tool create rely on an environment variable USYS96 to tell them where Uniface is installed. Create this variable now. For a default Uniface installation this might be C:\\Program Files (x86)\\Uniface\\Uniface 9.6.01\\
 * The tool can now be used by opening a command prompt in the root of the Uniface project you wish to setup and typing "projectsetup"

## Usage ##

### Available Template Substitutions ###

 * <project_name>: A unique name for this project. Used in the URL if it's a web project, so should only use URL safe characters
 * <project_path>: The path to the project in the developer's environment
 * <uniface_packages_path>: The path to the Uniface packages folder on the local machine
 * <uniface_path>:
 * <uniface_adm_path>:
 * <udbg_machine>:
 * <udbg_port>:
 * <urouter_machine>:
 * <urouter_port>:
 * <tomcat_port>:
 * <userver_user>:
 * <userver_password>:
 * <userver_password>:
 * <browser>:

### Project Setup Configuration File ###

 * templates: A list of templated files for the tool to copy and apply the template substitutions listed above
 * shortcuts: A list of shortcuts that the tool should create during setup
 * folders: A list of folders that the setup tool should create. These would usually be folders that the project needs but don't make sense to commit to version control. For example, a log folder.
 * build-switches: The switches to use when spawning the Uniface process to run the import and compilation of the project's source code:
    * asn: The assignment file to use, relative to the project's working directory
    * ini: The ini file to use, relative to the project's working directory. Can be blank if not required.
    * debug: If set to 1 then the debugger will be launched before the build process starts to allow troubleshooting

 * do-import: Automatically import source code
 * do-compile: Run a full compile after importing everything
 * import-defaults: Import the Uniface defaults (if false then Uniface defaults should be included as part of the project source)

## Contributing to the project ##


## Contributors ##

 * James Rodger
 * Thomas Shore