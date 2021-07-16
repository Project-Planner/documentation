# Data Specification

This document outlines how the data is saved in xml format on the backend side. Note that saving the data in xml was one of the requirements. 

# Calendar 

Each calendar has its own file containing all appointments, mile stones and other calendar data, as well as inofrmation about the calendar owner and view and edit permissions.
Descriptions have to be limited to 250 chars (in Frontend and Backend). 

```xml
<calendar>
    <name val="Birthday_Calendar" />
    <owner val="ownerName" />
    <id val="ownerName/Birthday_Calendar" /> <!--this field must always be formed like this and it must be unique -> calendar name must be unique to user-->
    <permissions>
        <view>
            <user val="Kevin" />
            <user val="otherkevin" />
        </view>
        <edit>
            <user val="lol" />
            <user val="lol2" />
        </edit>
    </permissions>
    <desc>Lorem Ipsum.</desc> <!-- Has to be limited to 250 chars (in Frontend and Backend) -->
    <items>
        <appointments>
            <appointment id="1224-34-2322342-42-24-24">
                <name val="somename that works"/>
                <startDate val="1.4.1990"/>
                <startTime val="4:12" />
                <endTime val="5:12" />
                <endDate val="14.4.2021" />
                <desc>Lorem Ipsum.</desc> <!-- Has to be limited to 250 chars (in Frontend and Backend) -->
            </appointment>
            <appointment id="1224-34-2322342-42-24-24">
                <name val="somename that also works"/>
                <startDate val="1.4.1990"/>
                <startTime val="4:12" />
                <endTime val="5:12" />
                <endDate val="14.4.2021" />
                <desc>Lorem Ipsum.</desc> <!-- Has to be limited to 250 chars (in Frontend and Backend) -->
            </appointment>
        </appointments>
        <milestones>
            <milestone id="1224-34-2322342-42-24-24">
                <name val="somename"/>
                <duedate val="date"/>
                <duetime val="5:34"/>
                <desc>Some Milestone</desc>
            </milestone>
            <milestone id="1224-34-2322342-42-24-24">
                <name val="somename"/>
                <duedate val="date"/>
                <duetime val="5:34"/>
                <desc>Some Milestone</desc>
            </milestone>
        </milestones>
        <tasks>
            <task id="1224-34-2322342-42-24-24">
                <name val="name"/>
                <milestone id="id of the milestone"/>
                <startDate val="1.4.1990"/>
                <startTime val="4:12" />
                <duedate val="date"/>
                <duetime val="5:34"/>
                <desc>Dolor</desc>
                <subtasks>
                    <subtask id="1224-34-2322342-42-24-24">
                        <name val="someName"/>
                        <startDate val="1.4.1990"/>
                        <startTime val="4:12" />
                        <duedate val="date"/>
                        <duetime val="5:34"/>
                        <desc>sit amet</desc>
                    </subtask>
                    <subtask id="1224-34-2322342-42-24-24">
                        <name val="someName"/>
                        <startDate val="1.4.1990"/>
                        <startTime val="4:12" />
                        <duedate val="date"/>
                        <duetime val="5:34"/>
                        <desc>sit amet</desc>
                    </subtask>
                </subtasks>
            </task>
            <task id="1224-34-2322342-42-24-24">
                <name val="name"/>
                <milestone id="id of the milestone"/>
                <startDate val="1.4.1990"/>
                <startTime val="4:12" />
                <duedate val="date"/>
                <duetime val="5:34"/>
                <desc>Dolor</desc>
                <subtasks>
                    <subtask id="someID">
                        <name val="someName"/>
                        <startDate val="1.4.1990"/>
                        <startTime val="4:12" />
                        <duedate val="date"/>
                        <duetime val="5:34"/>
                        <desc>sit amet</desc>
                    </subtask>
                    <subtask id="someID">
                        <name val="someName"/>
                        <startDate val="1.4.1990"/>
                        <startTime val="4:12" />
                        <duedate val="date"/>
                        <duetime val="5:34"/>
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
    <name val="Guenther_Pascal" /> <!-- Has to be limited to (ASCII-)letters, numbers and -, _ (FE and BE)-->
    <items>
        <calendar perm="owner" href="Guenther_Pascal/Guenther_Pascal" />
        <calendar perm="view" href="Abc/defg" />
        <calendar perm="edit" href="OtherUser/OtherCalendar" />
    </items>
</user>
```

# Auth 

Each user will have login info. Login stores user names alongside the bcrypt password hash of the user. 

```xml
<login>
    <name val="Peter" />
    <hash val="trololol" />
</login>
```
