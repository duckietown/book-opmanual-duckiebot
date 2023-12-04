# Reset Dashboard

Sometimes the Dashboard's database can get corrupted due to an improper shutdown of the robot.
This can have different kinds of effects on the usability of the dashboard, going from flat out 
**404** errors, to **bad gateway**, to **permission errors**.
In many cases, a hard-reset of the database is enough for the problem to get fixed. 


## Reset database

```{warning}
Resetting the database will delete all custom data from the dashboard and you will be asked
to perform the first setup again.
```

The dashboard stores all its databases inside a Docker volume. 
Use the following commands to force a reset by removing such volume,

```bash
docker -H ROBOT_NAME.local stop dashboard 
docker -H ROBOT_NAME.local rm dashboard 
docker -H ROBOT_NAME.local volume rm duckietown_compose-data 
dts duckiebot update ROBOT_NAME
```

The last step will remake the dashboard container and regenerate a database in the process.
