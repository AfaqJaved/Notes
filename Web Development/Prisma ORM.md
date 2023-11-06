_Prisma is a new kind of ORM that fundamentally differs from traditional ORMs and doesn't suffer from many of the problems commonly associated with these_.


Object Oriented Way Of Dealing Things.  [[TypeOrm]]

![[Screenshot 2023-11-02 at 1.26.33 pm.png]]


# What is Different In Prisma❓
(uses Declarative Approach)

Prisma works fundamentally different compared to that. With Prisma, you define your models in the **declarative** [Prisma schema](https://www.prisma.io/docs/concepts/components/prisma-schema) which serves as the single source of truth for your database schema and the models in your programming language.


![[Screenshot 2023-11-02 at 1.31.08 pm.png]]


# Working of Prisma


![[diagram-export-02-11-2023-13_48_20.png]]



## Topics To Cover 

### Prisma Client

- Insert one or more records in Database.
- Get All Records
- Get All Records By Selecting only required Attributes.
- Get Records Based on id or multiple conditions
- Update Single or multiple Records.
- Delete Single or multiple Records

# Relations



### Referential actions
 
Referential actions determine what happens to a record when your application deletes or updates a related record.

 - Cascade
 - Restrict
 - NoAction
 - Set Null

## One To One

![[Screenshot 2023-11-05 at 12.22.17 pm.png]]

![[Screenshot 2023-11-05 at 12.22.56 pm.png]]!


![[Screenshot 2023-11-05 at 12.23.16 pm.png]]


## One To Many

![[Screenshot 2023-11-06 at 11.47.05 am.png]]

## Many To Many

