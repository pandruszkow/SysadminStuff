# Postgres tips and tricks

## Postgres DB desktop client (better than pgAdmin 4)

[DBeaver Community](https://dbeaver.io/) does a fantastic job of being a nicer Postgres GUI. It's a bit slow on virtual machines over X11 forwarding, but the native OS version runs smoothly. It's free for commercial use too.

## Increase the number of connections

1. Run the following command using `psql`:

       alter system set max_connections to 10000;
  
2. Restart the `postgres` service with `systemctl restart postgres`
3. If you wish, verify that the change took effect by running the query below and checking that the value for this setting is `10000` (or whatever you set it to above):
     
       select * from pg_settings where name like 'max_connections';
       
**Why this might be useful:** large amounts of Junit tests that try to access the database are tying up the available connections, causing some tests to fail with an exception.
