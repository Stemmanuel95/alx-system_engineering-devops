# ISSUE SUMMARY
On Tuesday 30th May,2023 around 4:30 am GMT I received an emergency call from
the IT department of a client that uses our insurance operational software.I
was told that they were getting some strange errors from the application
server's operational software when they try to print the daily production
report from the system. The error was soo strange that I needed to get to the
site before 5:30am that day to troubleshoot the system and figure out what
could be wrong and then fix the error before working hours start at 8:00am same
day.The impact was more serious upon analysis such that there was no recorded
data into the database of the software for the previous business day which was
29th May,2023.

# TIMELINE
* 5:30am - A server issue is detected,causing system inbuilt reports to throw
  empty data for records printed from the previous day.
* 6:30am - Further checks suggested that an immediate virtual environment be
  setup to move clients onto a new server in order to allow time for further
  troubleshooting on old servers
* 7:00am - The teams provisions one new server and the database setup is
  commenced
* 7:30am - Team attemps to export a dump file from old database server in order
  to install it unto the newly provisioned database server
* 8:00am - Default database sys roles are granted to newly created Admin user
  and databse connect,resource,DBA and other parameters are granted to this new
  Admin user created
* 8:10am - Database team starts to import data dump into newly provisioned
  server
* 8:45am - Datadump import is done successfully howerver database team realises
  that the database sequence are not updated therefore system keeps showing
  errors when transactions are being processed.
  9:00am -  Database team finally updates all database sequences to allow free
  flow of transactions into the system
  9:15am - Users are granted access to the newly provisioned database and asked
  to recapture old data from the previous data and as well conduct businesses
  for the current working day

  # IMPACT

