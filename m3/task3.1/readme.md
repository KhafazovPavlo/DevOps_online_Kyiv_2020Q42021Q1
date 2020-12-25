## Task3.1

### Descrption of **the database for the forum**:

There are registred **users** who create **topics** and **post** messages in these topics. This means that the database forum should consist of 3 tables: **users**, **topics**, **posts**.
 
![Image5](screenshots/Image5.jpg "Scheme")

![Image6](screenshots/Image6.jpg "Image6")

A **primary key** uniquely identifies each record in a table.
A **foreign key** is used to link tables together.
A **not null** means the column can not accept null values.
An **auto increment** allows a unique number to be generated automatically for new record.
**int** is a numeric data type.
**text** is a string data type.
**varchar** is a variable lenght string.

### Creating database and tables:

![Image4](screenshots/Image4.jpg "Image4")

### Filling in tables:

![Image7](screenshots/Image7.jpg "Image7")

### Constructing and executing operator SELECT:

![Image8](screenshots/Image8.jpg "Image8")

![Image9](screenshots/Image9.jpg "Image9")
	
![Image10](screenshots/Image10.jpg "Image10")

_When I was filling the table **topics** I've added several authors (id-authors) to one topic (topic-name), because of this one topic had several id-topic and authors. I've corrected this:_

![Image11](screenshots/Image11.jpg "Image11")

The following statement selects who created topic "bicicles":

![Image12](screenshots/Image12.jpg "Image12")

The following statement selects which messages "bicicles" topic author wrote:

![Image13](screenshots/Image13.jpg "Image13")

The following statement selects in which topics the author of the topic "about fishing" left messages:

![Image14](screenshots/Image14.jpg "Image14")

The following statement selects from tables topics and users, and joins the result:

![Image15](screenshots/Image15.jpg "Image15")

 all posts, what topics they relate to and the authors of these posts:

![Image16](screenshots/Image16.jpg "Image16")

The following statement selects all users and topics created by them (if the user has not created a topic, then - NULL):

![Image17](screenshots/Image17.jpg "Image17")

The following statement selects only those groups with more than two messages:

![Image18](screenshots/Image18.jpg "Image18")

### Other different SQL queries (DDL, DML, DCL):

![Image19](screenshots/Image19.jpg "Image19")

![Image20](screenshots/Image20.jpg "Image20")

![Image21](screenshots/Image21.jpg "Image21")

### Creating new user with different privileges:

_I had a issue with a validate_password plugin, to resolve this issue I've changed policy to low and special char count to 0._

![Image22](screenshots/Image22.jpg "Image22")

Granting a newuser with different privileges:

![Image23](screenshots/Image23.jpg "Image23")

![Image24](screenshots/Image24.jpg "Image24")

![Image25](screenshots/Image25.jpg "Image25")

![Image26](screenshots/Image26.jpg "Image26")

### Making backup of DB forum, deleting table posts, and restoring from backup:

![Image28](screenshots/Image28.jpg "Image28")

### Transfering local database to RDS AWS:

Creating RDS database and aditing inbound rules to allow public access:

![Image30](screenshots/Image30.jpg "Image30")

![Image31](screenshots/Image31.jpg "Image31")

![Image32](screenshots/Image32.jpg "Image32")

Connecting to RDS AWS:

 ![Image33](screenshots/Image33.jpg "Image33")
 
 ![Image34](screenshots/Image34.jpg "Image34")
 
 Snapshot:
 
 ![Image35](screenshots/Image35.jpg "Image35")
 
 ### Working with DynamoDB (creating table, entering data, using query and scan):
 
![Image351](screenshots/Image351.jpg "Image351")

![Image36](screenshots/Image36.jpg "Image36")
  
![Image37](screenshots/Image37.jpg "Image37")

![Image38](screenshots/Image38.jpg "Image38")

![Image39](screenshots/Image39.jpg "Image39")

![Image40](screenshots/Image40.jpg "Image40")

