**File Permission** 
Linux file permissions define who can read, write, or execute a file or directory. These permissions apply to three types of users:

**Owner (User)** - The person who owns the file.

**Group** - A set of users who share access to the file.

**Others** - All other users.

**File Permission Structure:**

Permissions are represented by three sets of characters:

Owner Permissions (Position 1-3)

`r`: Read permission.

`w`: Write permission.

`x`: Execute permission.

`-`: No permission.

**Group Permissions (Position 4-6)**

 Same as above, but applies to users in the file's group.

**Other User Permissions (Position 7-9)**

Same as above, but applies to all other users.

**Access Control List (ACL):**
If there is an ACL applied, a `+` is shown at the end of the permission string (replacing the `.`). If no ACL is applied, it ends with a `.`.

ACLs provide more granular control over file permissions, allowing specific users or groups to have different permissions beyond the basic owner, group, and others model.

**Permission Assignment Methods:**

There are two primary methods to assign file permissions in Linux: **Symbolic Method** and **Numeric Method**.

1. **Symbolic Method:**
This method uses symbols (`r`, `w`, `x`, `+`, ``-, `=`) to modify permissions.

**Example**

<user_class><operation><permission> file.txt

**User Classes:**

`u`: User (Owner)
`g`: Group
`o`: Others
`a`: All (user, group, and others)

**Operations:**

`+`: Add permission
`-`: Remove permission
`=`: Set permission exactly (overwrite existing permissions)

**Permissions:**

`r`: Read
`w`: Write
`x`: Execute

**Examples:**

Add execute permission for the owner:


chmod u+x file.txt


**Remove write permission for others:**

bash

chmod o-w file.txt

**Set read and write permission for the group:**


chmod g=rw file.txt

2. **Numeric Method:**

This method uses numbers to represent permissions. Each permission type has a numeric value:

`4` = Read `(r)`
`2` = Write `(w)`
`1` = Execute `(x)`

Permissions are assigned by adding up the corresponding values for each class (owner, group, others).

**Examples:**

**Set read and write permission for the owner, and read permission for the group and others:**

chmod 644 file.txt

Breakdown:

Owner: Read (4) + Write (2) = 6
Group: Read (4) = 4
Others: Read (4) = 4

**Set full permission (read, write, and execute) for the owner, and read and execute permission for the group and others:**

chmod 755 file.txt

Breakdown:

Owner: Read (4) + Write (2) + Execute (1) = 7

Group: Read (4) + Execute (1) = 5

Others: Read (4) + Execute (1) = 5

