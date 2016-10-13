This repository has a tool called `cr-update-reviewers` that takes a Gerrit
change on [cr.joyent.us](https://cr.joyent.us) and updates the commit message
for that change based on the approvals already there.  It will create a new
patchset for the change with the updated commit message.

Here's an example:

    $ ./bin/cr-update-reviewers 684
    Change 684 current commit message:
    ----------------------------------------------
    joyent/node-fast#2 update dependencies to support Node v4
    ----------------------------------------------
    
    +1s found in Gerrit:
        Code-Review          Brian Bennett <brian.bennett@joyent.com>
        Integration-Approval Alex Wilson <alex.wilson@joyent.com>
    
    Suggested commit message:
    ------------------------------------------------
    joyent/node-fast#2 update dependencies to support Node v4
    Reviewed by: Brian Bennett <brian.bennett@joyent.com>
    Approved by: Alex Wilson <alex.wilson@joyent.com>
    ------------------------------------------------
    
    Create a new patchset with the suggested commit message? (y/[n]) 
    Cloning joyent/node-fast to /var/tmp/cr-update-reviewers.32942.
    Fetching patchset reference refs/changes/84/684/1.
    Checking out patchset reference refs/changes/84/684/1.
    Amending commit.
    Pushing new patchset: git push origin HEAD:refs/changes/684
    remote: Processing changes: updated: 1, refs: 1, done            
    remote: (W) 2f8b6fe: no files changed, message updated        
    remote: 
    remote: Updated Changes:        
    remote:   https://cr.joyent.us/684 joyent/node-fast#2 update dependencies to support Node v4 Reviewed by: Brian ...        
    remote: 
    To git+ssh://cr.joyent.us/joyent/node-fast.git
     * [new branch]      HEAD -> refs/changes/684
    
    Cleaning up: rm -rf /var/tmp/cr-update-reviewers.32942

Note that there's a bug that sometimes causes it to hang on input even after
you've answered the question.  If you hit enter again, it should proceed.
