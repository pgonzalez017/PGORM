#PGORM

This is Patrick Gonzalez's ORM

##Project Description

This ORM currently has support for creating entities and storing them 
into a relational database that utilizes PostgreSQL. All of the CRUD operations
are fully supported. One to one, many to one,
one to many, and many to many relations are not supported yet.


## Technologies Used

PostgreSQL, JUnit, Mockito, JPA, Reflections, HikariCP

##  Features
List of features ready and TODOs for future development

* Store Objects that you create into a table programmatically.
* Ability to perform of the CRUD operations on your entities.

To-do list:
 * Add the ability for one to one relationships between entities
 * Add the ability for one to many and many to one relationships between entities
 * Add the ability for many to many relationships between entities
 * Add the ability to work with any kind of SQL Language

#Getting Started

First in order to get the ORM just clone the git repo and grab the jar.

git clone https://github.com/pgonzalez017/PGORM.git

Add the jar as a dependency to your project and you're done.

#Usage

You can set your database connection properties in the connection.properties file

A few things to note when creating a class that you want to be
persisted to the database you must use the @Entity annotation above the
class.

Also you must use the @Id annotation on a primitive int variable
with the name id such as this:

@Id @GeneratedValue
private int id

The ORM is able to create a primary key for the table using
this variable.

Anytime you create a class that is denoted as an entity
you must create a static boolean variable with the name tableExists
that is initialized to false such as the one given:
private static boolean tableExists = false;

This variable is used to check if the table for the entity has already been created
I did this to avoid extra overhead of going to the database
and checking to see if the table exists there.

All entities must have a no args constructor and every field
that you intend to store into the database for the table of that entity
must have the @Column annotation above it along with a name

Example:
@Column(name="firstname")
private String firstName;

All entities must have a toString method.

