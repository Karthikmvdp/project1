import sys
import _mysql

import MySQLdb as mdb

DB_HOST = 'testdb.czfmk81u1m4b.us-west-1.rds.amazonaws.com'
DB_USER = 'admin'
DB_PASSWORD = 'passw0rd'
DB_NAME = 'testdb'


def _mysql_get_version():
    """
    _mysql implements the mysql C api directly.
    Actually recommended to use MySQLdb which is a wrapper over _mysql module
    """
    con = None    
    try:
        con = _mysql.connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)        
        con.query("SELECT VERSION()")
        result = con.use_result()
        print "MYSQL version: %s" % result.fetch_row()[0]
    except _mysql.Error, e:
        print "Error %d: %s" % (e.args[0], e.args[1])
        sys.exit(1)        
    finally:
        if con:
            con.close()



def create_and_populate():
    """
    Create a table for writers and insert some data into it
    """
    con = mdb.connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    
    with con:
        cur = con.cursor()
        sql = "CREATE TABLE writers (id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(23))"
        cur.execute(sql)
        
        # insert some data
        writers = ['Jack London', 'Honore de Balzac', 'Lion Feuchtwanger', 'Emile Zola', 'Truman Capote']
        
        for name in writers:
            cur.execute("INSERT INTO writers (NAME) VALUES ('%s')" % name

result = _mysql_get_version()
result2 = create_and_populate()
