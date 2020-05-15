This module uses db-migrate to elevate database scripts in NodeJS for postgres.
################################
ADDING A NEW DB CHANGE
################################
- Install db-migrate locally. This needs to done once. If its already installed skip this step. npm install db-migrate -g
- Install all dependency. npm install
- To add a new DB change run the below command. A change name must be unique and without contain space. 
`db-migrate create <change name> --config database.json -e local --sql-file`
- The above would have generated a couple of files under `./migrations/` directory. Now you need to go to ./migrations/sqls/<timestamp>-<change set id>-up.sql and ./migrations/sqls/<timestamp>-<change set id>-down.sql 
Example: ./migrations/sqls/20200507083241-initial-setup-up.sql & ./migrations/sqls/20200507083241-initial-setup-down.sql
Make sure no other changes are made and both up and down SQL files are having the query and rollback scripts.

################################
TESTING THE DB CHANGE LOCALLY
################################

Make sure you have a local postgres running. If not install postgres server locally and create a database using pgAdmin.
Export below environment variables in your terminal/cmd. In Mac/Ubuntu try export but in Windows you may have to use SET in place of export.
- `export DB_USER=<DB Username>`
- `export DB_PASSWORD=<DB Password>` 
- `export DB_HOST=localhost` 
- `export DB_PORT=5432`

Install all dependency. 
- `npm install`
- `db-migrate up --config database.sample.json -e local`
