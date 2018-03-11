posh-p4
=======

Perforce PowerShell integration. Prompt info and command line autocompletion

 - __Prompt for Perforce workspaces__
 
   Show the current depot and the state of files (additions, modifications, deletions) within prompt

 - __Tab completion__
 
   Provides tab completion for common commands when using perforce.
   
   E.g. `p4 a<tab>` --> `p4 add`


Usage
-----

See `profile.example.ps1` as to how you can integrate the tab completion and/or git prompt into your own profile.


If prompt shows a ! instead of the depot tree, it means you have too many views sync to the same folder. Script is limited to 1.

It could also mean your are not connected to perforce. try command `p4 where ...`


Note on performance: If you navigate at the root of a large repo, prompt will be slow.

posh-p4 uses `p4 status ...` to know which are files to add or to delete.. there might be other commands that are faster


Installing via OneGet
--------------------

run in powershell command:

```
Install-Module posh-p4 -Scope CurrentUser -AllowClobber
```


Installing manually
--------------------

Create folder C:\Users\<UserName>\Documents\WindowsPowerShell\Modules\posh-p4

Copy all files from this repo there.

run command:

```
Install-Module posh-p4
```


The Prompt
----------

PowerShell generates its prompt by executing a `prompt` function, if one exists.

An example of such a function is in `profile.example.ps1`

    C:\Users\mydepot\project p4:(//depot/project)>

* when depot path is Green, it means you are sync with the latest submit on this folder
* when depot path is Red, there is newer(s) submit
* whend depot path is Cyan, perforce server was too long to tell status so posh-p4 skiped answer in order to not take too long to display the prompt

By default, the status summary has the following format:

    [+A ~B -C]

ABC represent the working directory

 * `+` = Added files
 * `~` = Modified files
 * `-` = Removed files

if there is a `?` instead of a number, it means perforce server took too much time to answer

Inspired by
-----------

- posh-git
- posh-npm
- oh-my-zsh <3


License
--------

Microsoft Public License https://opensource.org/licenses/MS-PL
