SQLScribe
=========
This script allows the generation and reverse engineering of SQL from a database. The reverse engineering part is based on the SchemaSpy open source tool.

Two levels of abstration
* Conceptual model
* Relational model
* 

SQL Reverse Engineering (SQLScribeRev)
--------------------------------------
### Principle
Two steps:
* from database to modelio "relational model"
** based on SchemaSpy (http://schemaspy.sourceforge.net)
** reading the xml file produced by SchemaSpy into modelio thanks to ElementTree library

### Tests
Test cases 
* "library" example from SchemaSpy
** Source file directly available from  http://schemaspy.sourceforge.net/sample/library.xml
** Output that should be generated provided as an exemple in CyberBibliotheque project
* simple atomic examples
** one example per features, e.g.
*** two empty tables,
*** two tables with columns and keys, 
*** two tables with a foreign key constraints
*** ...
** both source file (database then .xml or just .xml) and modelio output should be built
* other tests cases to be build
** open source components with database (e.g. mediawiki, joomla, fusionforge, ...)
** (1) reverse the database with SchemaSpy to produce a .xml
** (2) test the SQLScribeRev reverse engineering tool

    <database name="library" type="MySQL - 5.1.35-community">
      <tables>
        <table name="address" numRows="9" remarks="Address details" type="TABLE">
          <column autoUpdated="true" digits="0" id="0" name="addressId" 
                  nullable="false" remarks="" size="10" type="INT">
            <child column="address" foreignKey="borrower_ibfk_1" implied="false"      
                   onDeleteCascade="false" table="borrower"/>
            <child column="address" foreignKey="library_branch_ibfk_1" implied="false" 
                   onDeleteCascade="false" table="library_branch"/>
            <child column="address" foreignKey="publisher_ibfk_1" implied="false" 
                   onDeleteCascade="false" table="publisher"/>
          </column>
          <column autoUpdated="false" digits="0" id="1" name="address1" 
                  nullable="false" remarks="Address line 1" size="50" type="VARCHAR"/>
          <column autoUpdated="false" digits="0" id="2" name="address2" 
                  nullable="true" remarks="Address line 2 (optional)" size="50" type="VARCHAR"/>
          <column autoUpdated="false" digits="0" id="3" name="city" 
                  nullable="false" remarks="" size="30" type="VARCHAR"/>
          <column autoUpdated="false" digits="0" id="4" name="state" 
                  nullable="false" remarks="" size="2" type="CHAR"/>
          <column autoUpdated="false" digits="0" id="5" name="zip" 
                  nullable="false" remarks="Dash req'd for zip+4" size="10" type="VARCHAR"/>
          <primaryKey column="addressId" sequenceNumberInPK="1"/>
          <index name="PRIMARY" unique="true">
            <column ascending="true" name="addressId"/>
          </index>
        </table>
        <table name="author" numRows="9" remarks="" type="TABLE">
        ...
      </tables>
    </database>
    
Relational Profile
-----------
Definition of an relational profile within the local module
* initialisation
** if the stereotype are not existing creating them
** get the corresponding stereotype for further use



SQL Forward Engineering
-----------------------