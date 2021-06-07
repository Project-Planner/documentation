# Data

This document outlines how the data is saved in xml format on the backend side. Note that saving the data in xml was one of the requirements. 

# Calendar 

Each calendar has its own file containing all appointments, mile stones and other calandar data, as well as inofrmation about the calendar owner and view and edit permissions.

```xml
<calender>
    <name val="Birthday Calendar" />
    <owner href="ownerFile1" />
    <permissions>
        <group val="View">
            <user href="Kevin" />
        </group>
        <group val="Edit">
            <user href="lol" />
        </group>
    </permissions>
    <items>
        <appointment>
            <color val="#FF0000" />
            <start val="insertLongHere" />
            <end val="insertLongHere" />
            <cat val="Leisure" />
            <desc>Lorem Ipsum.</desc>
        </appointment>
        <milestone />
        <deadline />
    </items>
</calender>
```

# User 

Each user has their own file, listing all calendars the user has at least read access to.

```xml
<user>
    <name val="Günther Pascal" /> 
    <items>
        <calender href="file1" />
        <calender href="file2" />
        <calender href="file3" />
    </items>
</user>
```

# Auth 

Each user will have an entry in the auth file, of which there is only one. The auth file stores user names alongside the bcrypt password hash of the user. 

```xml
<auth>
    <items>
        <entry>
            <name val="Peter" />
            <hash val="trololol" />
        </entry>
        <entry>
            <name val="Günther" />
            <hash val="trololol" />
        </entry>
    </items>
</auth>
```
