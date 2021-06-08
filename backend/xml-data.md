# Data Specification

This document outlines how the data is saved in xml format on the backend side. Note that saving the data in xml was one of the requirements. 

# Calendar 

Each calendar has its own file containing all appointments, mile stones and other calendar data, as well as inofrmation about the calendar owner and view and edit permissions.
Descriptions have to be limited to 250 chars (in Frontend and Backend). 

```xml
<calendar>
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
        <appointments>
            <appointment>
                <name val="somename"/>
                <color val="#FF0000" />
                <start val="insertLongHere" />
                <end val="insertLongHere" />
                <cat val="Leisure" />
                <desc>Lorem Ipsum.</desc> <!-- Has to be limited to 250 chars (in Frontend and Backend) -->
            </appointment>
        </appointments>
        <milestones>
            <milestone id="someID">
                <name val="somename"/>
                <duedate val="date"/>
            </milestone>
        </milestones>
        <tasks>
            <task>
                <name val="name"/>
                <milestone id="id of the milestone"/>
                <duedate val="date"/>
                <desc>Dolor</desc>
                <subtasks>
                    <subtask>
                        <name val="someName"/>
                        <duedate val="date"/>
                        <desc>sit amet</desc>
                    </subtask>
                </subtasks>
            </task>
        </tasks>
    </items>
</calendar>
```

# User 

Each user has their own file, listing all calendars the user has at least read access to. 
User names have to be limited to (ASCII-)letters, numbers and +, -, _ (Frontend and Backend).

```xml
<user>
    <name val="Günther Pascal" /> <!-- Has to be limited to (ASCII-)letters, numbers and +, -, _ (FE and BE)-->
    <items>
        <calendar href="file1" />
        <calendar href="file2" />
        <calendar href="file3" />
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
