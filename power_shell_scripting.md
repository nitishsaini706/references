# power shell scripting 

## commands 

- basic format of commands is   VERB-NOUN
- .ps1 extension is used to save powershell scripts
- we need to use ise scripting enviroment , we can allow extra inputs valled parameters 
- cmdlet  is the name of eventlog

1.  start-transcript  = it stores session history in a file

2. get-help
3. get-command
4. get-member  - discover objects , property , methods , objects has properties like color size etc , it has methods like action specific to object amd event handlers , when event happens eg open , close etc
1. get-command -noun history

### cmdlets 
1. get-help < cmdlet-name >
    - -full : explains parameter
    - -examples: show examples
    - get-help * - shows all 

2. to find a command 
    - to find using service get-command -noun services
    - to find using modules get-command -module vmware
    - we ca shoten the command using alias 
    - default copy or cp
    - get-alias give us list of all alias
    - get-alias -definition get-service   - check if alias exist 
    - to create alias  -  set-alias -name name -value select-string

3. some famous alias
    - cmdlet            alias     description
    - foreach-object    %       perform and opern agains each set of input objects
    - format-list       fl      formats output as list 
    - format-table      ft      format output as table
    - get-command       gcm     info about cmdlets
    - get-content       cat gs type     get contents  of item at loc 
    - get-process       gps ps          get process that is running 
    - get-help          help    
    - sort-object       sort
    - select-object     select
    - stop-process      kill    
    - write-object      echo write 

### synatx , variables

- by default execution policy is restricted we need to change it 
    - get-executionpolicy = to get current policy 
    - set-exectuionpolicy policy < name > = to set policy
    - het-help about_execution_policies 

- powershell.exe -exec bypass = to allow scripts to run 

### vairables 

- $a we use $ to set or use variable 
    - $a =7   set 
    - $A    output
    - $a = dir c:\
    - $a | sort-object -property name 
    - dir c:\  | sort name -desc 

- types , int string object
    - [int] $a = 7     explicit declaration
    - $ days = "sun","mon","tue"    collection of objects
    - we use index $days[0]   , we can use range(..)   [2..4]  [-1] for reverse  . $days.length   give no. of length

- special characters 
    - $_  : current pipeline object 
    - $ture, $false ,$null 
    - get-childitem variable : show them all 

- paranthesis( ) = used for loops , if and switch statements 
    - if($num gt 7){ "bigger than 7"}
    - foreach ( $f in $files ) { $f.name}

- curly braces { } = used as script blocks that is command inside other commands    
    - ls | %{ $_.length/1024 }   = print length of each file divided by 1024  

- quotes 
     - double and single are same except when variable is declared in one 
     - $a ="nitish"
     - write-host "hello i am $a " - hello i am nitish
     - if we use 'hello $a ' - hello $a 

- backtick ( ` ) it's escapes the dollar sign 