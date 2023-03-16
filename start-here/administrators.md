You need to give CDC Console access to someone else. No worries.

Click Administration > Administrators

Then, click the "Invite Administrator" button. Enter the email address and the group they should be associated with.

The "Group" is short for "Permission Group" which is set in "Permission Groups". If you are not happy with the "Permission Groups" you can "Create Group" and set the "privileges", "scope", "Data Field Access", and "Members" as needed.

_admins is a default group that gives access to everything in the CDC Console and allows one to invite anyone else - it cannot be deleted.

> Remind the person you are inviting to accept the invitation immediatly and finish the account creation proccess. The link expiration time is very short.

A person can be assigned to muliple groups. If you click the person's name in "Administrators" you will be able to see the groups they are associated with and there access level as shown below. You can also click "Assign Group" to add an additional Permission Group for a User. To remove a permission group, use the "TRASH ICON"

![The IP Address](/../assets/groups.png "Configuration Updates Only Checkbox in CDC Audit Log")


## Applications
Applications are also based on Permission Groups. It is best practice when using the API to not use the uerKey and secret associated with your CDC Account but use the userKey and secreat associated with an Application. This is best because if leave the company and your CDC Access is deleted, the application will stop working.